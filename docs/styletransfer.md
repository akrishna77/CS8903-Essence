---
layout: page
title: Style Transfer
---


```
# !pip install tensorflow==1.8.0
```


```
# !pip install tensorflow-gpu==1.8.0
```


```
# !wget https://developer.nvidia.com/compute/cuda/9.0/Prod/local_installers/cuda-repo-ubuntu1604-9-0-local_9.0.176-1_amd64-deb
# !dpkg -i cuda-repo-ubuntu1604-9-0-local_9.0.176-1_amd64-deb
# !apt-key add /var/cuda-repo-9-0-local/7fa2af80.pub
# !apt-get update
# !apt-get install cuda=9.0.176-1
```


```
# !nvcc --version
```

    nvcc: NVIDIA (R) Cuda compiler driver
    Copyright (c) 2005-2017 NVIDIA Corporation
    Built on Fri_Sep__1_21:08:03_CDT_2017
    Cuda compilation tools, release 9.0, V9.0.176



```
# !pip install scipy==1.1.0
```


```
from google.colab import drive
drive.mount('/content/drive')
```

    Drive already mounted at /content/drive; to attempt to forcibly remount, call drive.mount("/content/drive", force_remount=True).



```
from __future__ import print_function
from __future__ import division
from __future__ import absolute_import

# from imageio import imread, imwrite
# from skimage.transform import resize
from scipy.misc import imread, imresize, imsave
from scipy.optimize import fmin_l_bfgs_b
import numpy as np 
import time
import warnings
import os
from PIL import Image
import PIL.ImageOps
import tensorflow as tf

from tensorflow.python.keras._impl.keras.models import Model
from tensorflow.python.keras._impl.keras.engine import Input
from tensorflow.python.keras._impl.keras.layers.convolutional import Convolution2D, AveragePooling2D, MaxPooling2D
from tensorflow.python.keras._impl.keras import backend as K
from tensorflow.python.keras._impl.keras.utils.data_utils import get_file
from tensorflow.python.keras._impl.keras.utils.layer_utils import convert_all_kernels_in_model
from tensorflow.python.keras._impl.keras.applications.vgg16 import VGG16
```

    /usr/local/lib/python3.6/dist-packages/tensorflow/python/framework/dtypes.py:519: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
      _np_qint8 = np.dtype([("qint8", np.int8, 1)])
    /usr/local/lib/python3.6/dist-packages/tensorflow/python/framework/dtypes.py:520: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
      _np_quint8 = np.dtype([("quint8", np.uint8, 1)])
    /usr/local/lib/python3.6/dist-packages/tensorflow/python/framework/dtypes.py:521: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
      _np_qint16 = np.dtype([("qint16", np.int16, 1)])
    /usr/local/lib/python3.6/dist-packages/tensorflow/python/framework/dtypes.py:522: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
      _np_quint16 = np.dtype([("quint16", np.uint16, 1)])
    /usr/local/lib/python3.6/dist-packages/tensorflow/python/framework/dtypes.py:523: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
      _np_qint32 = np.dtype([("qint32", np.int32, 1)])
    /usr/local/lib/python3.6/dist-packages/tensorflow/python/framework/dtypes.py:528: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
      np_resource = np.dtype([("resource", np.ubyte, 1)])



<p style="color: red;">
The default version of TensorFlow in Colab will soon switch to TensorFlow 2.x.<br>
We recommend you <a href="https://www.tensorflow.org/guide/migrate" target="_blank">upgrade</a> now 
or ensure your notebook will continue to use TensorFlow 1.x via the <code>%tensorflow_version 1.x</code> magic:
<a href="https://colab.research.google.com/notebooks/tensorflow_version.ipynb" target="_blank">more info</a>.</p>




```
import warnings
warnings.filterwarnings('ignore')
```


```
TF_WEIGHTS_PATH_NO_TOP = 'https://github.com/fchollet/deep-learning-models/releases/download/v0.1/vgg16_weights_tf_dim_ordering_tf_kernels_notop.h5'

TF_19_WEIGHTS_PATH_NO_TOP = 'https://github.com/fchollet/deep-learning-models/releases/download/v0.1/vgg19_weights_tf_dim_ordering_tf_kernels_notop.h5'
```


```
def hex_to_rgb(h):
      hh = h.lstrip("#")
      rgb = tuple(int(hh[i:i+2], 16) for i in (0, 2 ,4))
      return rgb

def str_to_bool(v):
    return v.lower() in ("true", "yes", "t", "1")
```


```
home_dir = '/content/drive/My Drive/intricate-art-neural-transfer/'
base_image_path = home_dir + 'silhouettes/adventurous.jpg'
style_reference_image_paths = [home_dir + 'style/geometric_mixedcolors7_nofilter_46.png']
result_prefix = home_dir + 'results/color_adventurous'
num_iter = 25
```


```
content_weight = 0.025
total_variation_weight = 8.5e-5
style_weight = [1]
style_scale = 1.0
content_loss_type = 0
img_size = 600
model = "vgg16"
content_layer = "block5_conv2"
init_image = "content"
pool = "max"
rescale_method = "bilinear"
rescale_image = str_to_bool("False")
maintain_aspect_ratio = str_to_bool("True")
bg_color = hex_to_rgb('#ffffff')
min_improvement = 0.0
bg_image = None

silhouette = Image.open(base_image_path).convert('L')
inverted_silhouette = PIL.ImageOps.invert(silhouette)

style_image_paths = []
for style_image_path in style_reference_image_paths:
    style_image_paths.append(style_image_path)

style_weights = []

if len(style_image_paths) != len(style_weight):
    print("Mismatch in number of style images provided and number of style weights provided. \n"
          "Found %d style images and %d style weights. \n"
          "Equally distributing weights to all other styles." % (len(style_image_paths), len(style_weight)))

    weight_sum = sum(style_weight) * style_scale
    count = len(style_image_paths)

    for i in range(len(style_image_paths)):
        style_weights.append(weight_sum / count)
else:
    for style_weight in style_weight:
        style_weights.append(style_weight * style_scale)

# Decide pooling function
pooltype = str(pool).lower()
assert pooltype in ["ave", "max"], 'Pooling argument is wrong. Needs to be either "ave" or "max".'

pooltype = 1 if pooltype == "ave" else 0

read_mode = "gray" if init_image == "gray" else "color"

# dimensions of the generated picture.
img_width = img_height = 0

img_WIDTH = img_HEIGHT = 0
aspect_ratio = 0

assert content_loss_type in [0, 1, 2], "Content Loss Type must be one of 0, 1 or 2"

# util function to open, resize and format pictures into appropriate tensors
def preprocess_image(image_path, load_dims=False, read_mode="color"):
    global img_width, img_height, img_WIDTH, img_HEIGHT, aspect_ratio

    mode = "RGB" if read_mode == "color" else "L"
    img = imread(image_path, mode=mode)  # Prevents crashes due to PNG images (ARGB)

    if mode == "L":
        # Expand the 1 channel grayscale to 3 channel grayscale image
        temp = np.zeros(img.shape + (3,), dtype=np.uint8)
        temp[:, :, 0] = img
        temp[:, :, 1] = img.copy()
        temp[:, :, 2] = img.copy()

        img = temp

    if load_dims:
        img_WIDTH = img.shape[0]
        img_HEIGHT = img.shape[1]
        aspect_ratio = float(img_HEIGHT) / img_WIDTH

        img_width = img_size
        if maintain_aspect_ratio:
            img_height = int(img_width * aspect_ratio)
        else:
            img_height = img_size

    img = imresize(img, (img_width, img_height)).astype('float32')

    # RGB -> BGR
    img = img[:, :, ::-1]

    img[:, :, 0] -= 103.939
    img[:, :, 1] -= 116.779
    img[:, :, 2] -= 123.68

    img = np.expand_dims(img, axis=0)
    return img


# util function to convert a tensor into a valid image
def deprocess_image(x):
    x = x.reshape((img_width, img_height, 3))

    x[:, :, 0] += 103.939
    x[:, :, 1] += 116.779
    x[:, :, 2] += 123.68

    # BGR -> RGB
    x = x[:, :, ::-1]

    x = np.clip(x, 0, 255).astype('uint8')
    return x


def load_mask_sil(invert_sil, shape):
    width, height, _ = shape
    invert_array = np.array(invert_sil.convert('L'))
    mask = imresize(invert_sil, (width, height), interp='bicubic').astype('float32')

    # Perform binarization of mask
    mask[mask <= 127] = 0
    mask[mask > 128] = 255

    max = np.amax(mask)
    mask /= max

    return mask

  

# util function to apply mask to generated image
def mask_content(content_path, generated, mask, bg_color=bg_color):
    content_image = imread(content_path, mode='RGB')
    content_image = imresize(content_image, (img_width, img_height), interp='bicubic')
    width, height, channels = generated.shape
    if bg_image is not None:
        background_image = imread(bg_image, mode='RGB')
        background_image = imresize(background_image, (img_width, img_height), interp='bicubic')
        for i in range(width):
            for j in range(height):
                if mask[i,j] == 0:
                    generated[i, j, :] = background_image[i, j, :]
    else:
        for i in range(width):
            for j in range(height):
                if mask[i, j] == 0.:
                    for k in range(3):
                        generated[i,j][k] = bg_color[k]

    return generated



def pooling_func(x):
    if pooltype == 1:
        return AveragePooling2D((2, 2), strides=(2, 2))(x)
    else:
        return MaxPooling2D((2, 2), strides=(2, 2))(x)


# get tensor representations of our images
base_image = K.variable(preprocess_image(base_image_path, True, read_mode=read_mode))

style_reference_images = []
for style_path in style_image_paths:
    style_reference_images.append(K.variable(preprocess_image(style_path)))

# this will contain our generated image
combination_image = K.placeholder((1, img_width, img_height, 3))

image_tensors = [base_image]
for style_image_tensor in style_reference_images:
    image_tensors.append(style_image_tensor)
image_tensors.append(combination_image)

nb_tensors = len(image_tensors)
print("nb_tensors", nb_tensors)
nb_style_images = nb_tensors - 2 # Content and Output image not considered

# combine the various images into a single Keras tensor
input_tensor = K.concatenate(image_tensors, axis=0)

shape = (nb_tensors, img_width, img_height, 3)
inp_shape = (img_width, img_height, 3)

ip = Input(tensor=input_tensor, batch_shape=shape)

model = VGG16(include_top=False, weights='imagenet', input_tensor = input_tensor,
              input_shape=inp_shape, pooling='max')

print('Model loaded.')

# get the symbolic outputs of each "key" layer (we gave them unique names).
outputs_dict = dict([(layer.name, layer.output) for layer in model.layers])
shape_dict = dict([(layer.name, layer.output_shape) for layer in model.layers])

# compute the neural style loss
# first we need to define 4 util functions

# Improvement 1
# the gram matrix of an image tensor (feature-wise outer product) using shifte, return_mask_img = Trued activations
def gram_matrix(x):
    assert K.ndim(x) == 3
    features = K.batch_flatten(K.permute_dimensions(x, (2, 0, 1)))
    gram = K.dot(features - 1, K.transpose(features - 1))
    return gram


# the "style loss" is designed to maintain
# the style of the reference image in the generated image.
# It is based on the gram matrices (which capture style) of
# feature maps from the style reference image
# and from the generated image

def style_loss(style, combination, nb_channels=None):
    assert K.ndim(style) == 3
    assert K.ndim(combination) == 3

    S = gram_matrix(style)
    C = gram_matrix(combination)
    channels = 3
    size = img_width * img_height
    return K.sum(K.square(S - C)) / (4. * (channels ** 2) * (size ** 2))


# an auxiliary loss function
# designed to maintain the "content" of the
# base image in the generated image
def content_loss(base, combination):
    channel_dim = -1

    try:
        channels = K.int_shape(base)[channel_dim]
    except TypeError:
        channels = K.shape(base)[channel_dim]
    size = img_width * img_height

    if content_loss_type == 1:
        multiplier = 1. / (2. * (channels ** 0.5) * (size ** 0.5))
    elif content_loss_type == 2:
        multiplier = 1. / (channels * size)
    else:
        multiplier = 1.

    return multiplier * K.sum(K.square(combination - base))


# the 3rd loss function, total variation loss,
# designed to keep the generated image locally coherent
def total_variation_loss(x):
    assert K.ndim(x) == 4
    a = K.square(x[:, :img_width - 1, :img_height - 1, :] - x[:, 1:, :img_height - 1, :])
    b = K.square(x[:, :img_width - 1, :img_height - 1, :] - x[:, :img_width - 1, 1:, :])
    return K.sum(K.pow(a + b, 1.25))

if model == "vgg19":
    feature_layers = ['block1_conv1', 'block1_conv2', 'block2_conv1', 'block2_conv2', 'block3_conv1', 'block3_conv2',
                  'block3_conv3', 'block3_conv4', 'block4_conv1', 'block4_conv2', 'block4_conv3', 'block4_conv4',
                  'block5_conv1', 'block5_conv2', 'block5_conv3', 'block5_conv4']
else:

    feature_layers = ['block1_conv1', 'block1_conv2', 'block2_conv1', 'block2_conv2', 'block3_conv1', 'block3_conv2',
                      'block3_conv3', 'block4_conv1', 'block4_conv2', 'block4_conv3', 'block5_conv1', 'block5_conv2',
                      'block5_conv3']

# combine these loss functions into a single scalar
loss = K.variable(0.)
layer_features = outputs_dict[content_layer]
base_image_features = layer_features[0, :, :, :]
combination_features = layer_features[nb_tensors - 1, :, :, :]
loss = loss + content_weight * content_loss(base_image_features,
                                      combination_features)
# Improvement 2
# Use all layers for style feature extraction and reconstruction
nb_layers = len(feature_layers) - 1

channel_index =  -1

# Improvement 3 : Chained Inference without blurring
for i in range(len(feature_layers) - 1):
    layer_features = outputs_dict[feature_layers[i]]
    shape = shape_dict[feature_layers[i]]
    combination_features = layer_features[nb_tensors - 1, :, :, :]
    style_reference_features = layer_features[1:nb_tensors - 1, :, :, :]
    sl1 = []
    for j in range(nb_style_images):
        sl1.append(style_loss(style_reference_features[j], combination_features,  shape))

    layer_features = outputs_dict[feature_layers[i + 1]]
    shape = shape_dict[feature_layers[i + 1]]
    combination_features = layer_features[nb_tensors - 1, :, :, :]
    style_reference_features = layer_features[1:nb_tensors - 1, :, :, :]
    sl2 = []
    for j in range(nb_style_images):
        sl2.append(style_loss(style_reference_features[j], combination_features, shape))
        

    for j in range(nb_style_images):
        sl = sl1[j] - sl2[j]

        # Improvement 4
        # Geometric weighted scaling of style loss
        loss += (style_weights[j] / (2 ** (nb_layers - (i + 1)))) * sl

loss += total_variation_weight * total_variation_loss(combination_image)

# get the gradients of the generated image wrt the loss
grads = K.gradients(loss, combination_image)

outputs = [loss]
if type(grads) in {list, tuple}:
    outputs += grads
else:
    outputs.append(grads)

f_outputs = K.function([combination_image], outputs)


def eval_loss_and_grads(x):
    x = x.reshape((1, img_width, img_height, 3))
    outs = f_outputs([x])
    loss_value = outs[0]
    if len(outs[1:]) == 1:
        grad_values = outs[1].flatten().astype('float64')
    else:
        grad_values = np.array(outs[1:]).flatten().astype('float64')
    return loss_value, grad_values


# this Evaluator class makes it possible
# to compute loss and gradients in one pass
# while retrieving them via two separate functions,
# "loss" and "grads". This is done because scipy.optimize
# requires separate functions for loss and gradients,
# but computing them separately would be inefficient.
class Evaluator(object):
    def __init__(self):
        self.loss_value = None
        self.grads_values = None

    def loss(self, x):
        assert self.loss_value is None
        loss_value, grad_values = eval_loss_and_grads(x)
        self.loss_value = loss_value
        self.grad_values = grad_values
        return self.loss_value

    def grads(self, x):
        assert self.loss_value is not None
        grad_values = np.copy(self.grad_values)
        self.loss_value = None
        self.grad_values = None
        return grad_values


evaluator = Evaluator()

# run scipy-based optimization (L-BFGS) over the pixels of the generated image
# so as to minimize the neural style loss


if "content" in init_image or "gray" in init_image:
    x = preprocess_image(base_image_path, True, read_mode=read_mode)
elif "noise" in init_image:
    x = np.random.uniform(0, 255, (1, img_width, img_height, 3)) - 128.

else:
    print("Using initial image : ", init_image)
    x = preprocess_image(init_image, read_mode=read_mode)


prev_min_val = -1

improvement_threshold = float(min_improvement)

for i in range(num_iter):
    print("Starting iteration %d of %d" % ((i + 1), num_iter))
    start_time = time.time()

    x, min_val, info = fmin_l_bfgs_b(evaluator.loss, x.flatten(), fprime=evaluator.grads, maxfun=20)

    if prev_min_val == -1:
        prev_min_val = min_val

    improvement = (prev_min_val - min_val) / prev_min_val * 100

    print("Current loss value:", min_val, " Improvement : %0.3f" % improvement, "%")
    prev_min_val = min_val
    # save current generated image
    img = deprocess_image(x.copy())

    if not rescale_image:
        img_ht = int(img_width * aspect_ratio)
        print("Rescaling Image to (%d, %d)" % (img_width, img_ht))
        img = imresize(img, (img_width, img_ht), interp=rescale_method)

    if rescale_image:
        print("Rescaling Image to (%d, %d)" % (img_WIDTH, img_HEIGHT))
        img = imresize(img, (img_WIDTH, img_HEIGHT), interp=rescale_method)
    
    if i == num_iter-1:
        fname = result_prefix + ".png"

        mask = load_mask_sil(inverted_silhouette, img.shape)
        final_img = mask_content(base_image_path, img, mask)
        end_time = time.time()
        imsave(fname, final_img)
        print("Image saved as", fname)
        print("Iteration %d completed in %ds" % (i + 1, end_time - start_time))

    if improvement_threshold is not 0.0:
        if improvement < improvement_threshold and improvement is not 0.0:
            print("Improvement (%f) is less than improvement threshold (%f). Early stopping script." %
                  (improvement, improvement_threshold))
            exit()
```

    nb_tensors 3
    Model loaded.
    Starting iteration 1 of 25
    Current loss value: 148802750.0  Improvement : 0.000 %
    Rescaling Image to (600, 600)
    Starting iteration 2 of 25
    Current loss value: 33875748.0  Improvement : 77.234 %
    Rescaling Image to (600, 600)
    Starting iteration 3 of 25
    Current loss value: 14851167.0  Improvement : 56.160 %
    Rescaling Image to (600, 600)
    Starting iteration 4 of 25
    Current loss value: 7322995.0  Improvement : 50.691 %
    Rescaling Image to (600, 600)
    Starting iteration 5 of 25
    Current loss value: 4479878.0  Improvement : 38.825 %
    Rescaling Image to (600, 600)
    Starting iteration 6 of 25
    Current loss value: 3097642.8  Improvement : 30.854 %
    Rescaling Image to (600, 600)
    Starting iteration 7 of 25
    Current loss value: 2371242.8  Improvement : 23.450 %
    Rescaling Image to (600, 600)
    Starting iteration 8 of 25
    Current loss value: 1927988.6  Improvement : 18.693 %
    Rescaling Image to (600, 600)
    Starting iteration 9 of 25
    Current loss value: 1652229.5  Improvement : 14.303 %
    Rescaling Image to (600, 600)
    Starting iteration 10 of 25
    Current loss value: 1471660.4  Improvement : 10.929 %
    Rescaling Image to (600, 600)
    Starting iteration 11 of 25
    Current loss value: 1342152.9  Improvement : 8.800 %
    Rescaling Image to (600, 600)
    Starting iteration 12 of 25
    Current loss value: 1249477.0  Improvement : 6.905 %
    Rescaling Image to (600, 600)
    Starting iteration 13 of 25
    Current loss value: 1176939.5  Improvement : 5.805 %
    Rescaling Image to (600, 600)
    Starting iteration 14 of 25
    Current loss value: 1120541.4  Improvement : 4.792 %
    Rescaling Image to (600, 600)
    Starting iteration 15 of 25
    Current loss value: 1076238.2  Improvement : 3.954 %
    Rescaling Image to (600, 600)
    Starting iteration 16 of 25
    Current loss value: 1041447.7  Improvement : 3.233 %
    Rescaling Image to (600, 600)
    Starting iteration 17 of 25
    Current loss value: 1012218.3  Improvement : 2.807 %
    Rescaling Image to (600, 600)
    Starting iteration 18 of 25
    Current loss value: 987234.5  Improvement : 2.468 %
    Rescaling Image to (600, 600)
    Starting iteration 19 of 25
    Current loss value: 965538.3  Improvement : 2.198 %
    Rescaling Image to (600, 600)
    Starting iteration 20 of 25
    Current loss value: 945411.25  Improvement : 2.085 %
    Rescaling Image to (600, 600)
    Starting iteration 21 of 25
    Current loss value: 927834.5  Improvement : 1.859 %
    Rescaling Image to (600, 600)
    Starting iteration 22 of 25
    Current loss value: 912419.2  Improvement : 1.661 %
    Rescaling Image to (600, 600)
    Starting iteration 23 of 25
    Current loss value: 898394.6  Improvement : 1.537 %
    Rescaling Image to (600, 600)
    Starting iteration 24 of 25
    Current loss value: 886156.44  Improvement : 1.362 %
    Rescaling Image to (600, 600)
    Starting iteration 25 of 25
    Current loss value: 875270.4  Improvement : 1.228 %
    Rescaling Image to (600, 600)
    Image saved as /content/drive/My Drive/intricate-art-neural-transfer/results/color_adventurous.png
    Iteration 25 completed in 9s



```

```
