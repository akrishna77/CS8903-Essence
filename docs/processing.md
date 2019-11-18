---
layout: page
title: Processing
---

## Data -> Table


```python
import pandas as pd
from itertools import groupby
```


```python
descriptions =[]

with open("how_people_describe_themselves.txt","r")  as f:
    for i in f:
        descriptions.append(i.rstrip('\n'))
```


```python
desc_array = [list(group) for k, group in groupby(descriptions, lambda x: x == ' ') if not k]
    
```


```python
for i in desc_array:
    i[1] = i[1].strip('Who you are: ')
    i[2] = i[2].strip('What you are like: ')
    i[3] = i[3].strip('What is the essence of what makes you YOU: ')
```


```python
df = pd.DataFrame(desc_array, columns=['person', 'who', 'likes', 'essence'])
df[:10]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>person</th>
      <th>who</th>
      <th>likes</th>
      <th>essence</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>Person 1</td>
      <td>I am a 28-year-old woman living in Massachusetts.</td>
      <td>I'm neurotic and eccentric but good at heart.</td>
      <td>I am obsessed with rabbits and love technology.</td>
    </tr>
    <tr>
      <td>1</td>
      <td>Person 2</td>
      <td>I am dedicated and persistent and willing to g...</td>
      <td>'m fun loving and like to make people laugh by...</td>
      <td>I am insightful and am able to fit together pi...</td>
    </tr>
    <tr>
      <td>2</td>
      <td>Person 3</td>
      <td>I am a feminist, a student, and a homosexual.</td>
      <td>I am kind, nurturing, caring, and genuine.</td>
      <td>My honesty, my loyalty, and my generosity make...</td>
    </tr>
    <tr>
      <td>3</td>
      <td>Person 4</td>
      <td>I'm an immigrant who became a citizen of the U...</td>
      <td>I can be stubborn and stand-offish, but I stil...</td>
      <td>I'm introverted, so I need time alone to recha...</td>
    </tr>
    <tr>
      <td>4</td>
      <td>Person 5</td>
      <td>I'm a boring person</td>
      <td>I'm quiet and introspective.</td>
      <td>I have deep wells of sorrow.</td>
    </tr>
    <tr>
      <td>5</td>
      <td>Person 6</td>
      <td>I am a girl who lives in New York City in my t...</td>
      <td>I am very social and outgoing.</td>
      <td>I am outgoing and care tremendously about my f...</td>
    </tr>
    <tr>
      <td>6</td>
      <td>Person 7</td>
      <td>I am a mom of 3</td>
      <td>I like R &amp;B Music, Japanese Food, Pizz</td>
      <td>I am sympathetic.</td>
    </tr>
    <tr>
      <td>7</td>
      <td>Person 8</td>
      <td>I am a licensed counselor.</td>
      <td>I'm silly and funny.</td>
      <td>I'm fun and sarcastic a lot of the time.</td>
    </tr>
    <tr>
      <td>8</td>
      <td>Person 9</td>
      <td>I'm Jim, a 53 year old american man</td>
      <td>I'm forceful, happy, calm and occasionally gru...</td>
      <td>I'm a drivan dominant at work and play. My wif...</td>
    </tr>
    <tr>
      <td>9</td>
      <td>Person 10</td>
      <td>I'm a fat, biracial bisexual woman.</td>
      <td>I'm a funny depressive--aren't all depressives...</td>
      <td>I'm a boring drudge, not glamorous or fancy, b...</td>
    </tr>
  </tbody>
</table>
</div>



## NLP


```python
import nltk
from nltk.corpus import stopwords
from spellchecker import SpellChecker

nltk.download('stopwords')
spell = SpellChecker()
```

    [nltk_data] Downloading package stopwords to
    [nltk_data]     /Users/akrishna/nltk_data...
    [nltk_data]   Package stopwords is already up-to-date!



```python
def preprocess(text):
    """Pre-processes the text, splits into tokens that are lower-cased, filtered and lemmatized."""
    tokens = (t.lower() for t in nltk.word_tokenize(text)
                            if t.isalpha()
                            and t.lower() not in stopwords.words())

    # wordnet_lemmatizer = nltk.WordNetLemmatizer()
    return [spell.correction(t) for t in tokens]
```


```python
pos_tagged_desc = []
for i in desc_array:
    x = [nltk.pos_tag(preprocess(i[1])), nltk.pos_tag(preprocess(i[2])), nltk.pos_tag(preprocess(i[3]))]
    pos_tagged_desc.append(x)
```


```python
pos_tagged_desc[0]
```




    [[('woman', 'NN'), ('living', 'VBG'), ('massachusetts', 'NNS')],
     [('neurotic', 'JJ'), ('eccentric', 'RB'), ('good', 'JJ'), ('heart', 'NN')],
     [('obsessed', 'VBN'),
      ('rabbits', 'NNS'),
      ('love', 'VBP'),
      ('technology', 'NN')]]




```python
descriptors = []
for i in pos_tagged_desc:
    s = ""
    for j in i:
        for k in j:
            s += k[0]+" "
    descriptors.append(s)
```


```python
descriptors[:5]
```




    ['woman living massachusetts neurotic eccentric good heart obsessed rabbits love technology ',
     'dedicated persistent willing go extra mil fun loving like make people laugh telling jokes making light situations insightful able fit together pieces understand big picture ',
     'feminist student homosexual kind nurturing caring genuine honesty loyalty generosity make ',
     'immigrant became citizen united states american stubborn still much friends family nerd love video games prefer stay home introverted need time alone recharge calibrate ',
     'boring person quiet introspective deep wells sorrow ']



## TF-IDF


```python
from sklearn.feature_extraction.text import TfidfVectorizer
```

#### For each description as a document


```python
vectorizer = TfidfVectorizer(use_idf=True)
X = vectorizer.fit_transform(descriptors)

df_idf = pd.DataFrame(X[0].T.todense(), index=vectorizer.get_feature_names(),columns=["idf_weights"]).sort_values('idf_weights', ascending=False)[:20]
df_idf.sort_values(by=['idf_weights'], ascending=False)[:10]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>idf_weights</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>technology</td>
      <td>0.327801</td>
    </tr>
    <tr>
      <td>obsessed</td>
      <td>0.327801</td>
    </tr>
    <tr>
      <td>massachusetts</td>
      <td>0.327801</td>
    </tr>
    <tr>
      <td>living</td>
      <td>0.327801</td>
    </tr>
    <tr>
      <td>eccentric</td>
      <td>0.327801</td>
    </tr>
    <tr>
      <td>rabbits</td>
      <td>0.327801</td>
    </tr>
    <tr>
      <td>neurotic</td>
      <td>0.327801</td>
    </tr>
    <tr>
      <td>heart</td>
      <td>0.296444</td>
    </tr>
    <tr>
      <td>good</td>
      <td>0.274196</td>
    </tr>
    <tr>
      <td>woman</td>
      <td>0.230918</td>
    </tr>
  </tbody>
</table>
</div>



#### For each of the questions as a document


```python
who = []
likes = []
essence = []
for i in range(len(pos_tagged_desc)):
        who.append(pos_tagged_desc[i][0])
        likes.append(pos_tagged_desc[i][1])
        essence.append(pos_tagged_desc[i][2])
```


```python
who_list = []
for i in who:
    s = ""
    for j in i:
            s += j[0]+" "
    who_list.append(s)
    
likes_list = []
for i in likes:
    s = ""
    for j in i:
            s += j[0]+" "
    likes_list.append(s)
    
essence_list = []
for i in essence:
    s = ""
    for j in i:
            s += j[0]+" "
    essence_list.append(s)
```


```python
vectorizer = TfidfVectorizer(use_idf=True)
X = vectorizer.fit_transform(who_list)

df_idf = pd.DataFrame(X[0].T.todense(), index=vectorizer.get_feature_names(),columns=["idf_weights"]).sort_values('idf_weights', ascending=False)[:20]
df_idf.sort_values(by=['idf_weights'], ascending=False)[:3]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>idf_weights</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>living</td>
      <td>0.632931</td>
    </tr>
    <tr>
      <td>massachusetts</td>
      <td>0.632931</td>
    </tr>
    <tr>
      <td>woman</td>
      <td>0.445865</td>
    </tr>
  </tbody>
</table>
</div>




```python
vectorizer = TfidfVectorizer(use_idf=True)
X = vectorizer.fit_transform(likes_list)

df_idf = pd.DataFrame(X[0].T.todense(), index=vectorizer.get_feature_names(),columns=["idf_weights"]).sort_values('idf_weights', ascending=False)[:20]
df_idf.sort_values(by=['idf_weights'], ascending=False)[:3]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>idf_weights</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>neurotic</td>
      <td>0.51179</td>
    </tr>
    <tr>
      <td>eccentric</td>
      <td>0.51179</td>
    </tr>
    <tr>
      <td>heart</td>
      <td>0.51179</td>
    </tr>
  </tbody>
</table>
</div>




```python
vectorizer = TfidfVectorizer(use_idf=True)
X = vectorizer.fit_transform(essence_list)

df_idf = pd.DataFrame(X[0].T.todense(), index=vectorizer.get_feature_names(),columns=["idf_weights"]).sort_values('idf_weights', ascending=False)[:20]
df_idf.sort_values(by=['idf_weights'], ascending=False)[:3]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>idf_weights</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>technology</td>
      <td>0.53816</td>
    </tr>
    <tr>
      <td>obsessed</td>
      <td>0.53816</td>
    </tr>
    <tr>
      <td>rabbits</td>
      <td>0.53816</td>
    </tr>
  </tbody>
</table>
</div>



## RAKE


```python
# !pip install rake-nltk
```


```python
from rake_nltk import Rake, Metric

r = Rake(ranking_metric=Metric.DEGREE_TO_FREQUENCY_RATIO)
r.extract_keywords_from_text(desc_array[0][1])
r.get_ranked_phrases()
```

## Top-3


```python
top3 = []
for i in X:
    top3_desc = pd.DataFrame(i.T.todense(), index=vectorizer.get_feature_names(),columns=["idf_weights"]).sort_values('idf_weights', ascending=False)
    top3.append(top3_desc.index[:3].tolist())
```


```python
top3[:5]
```




    [['technology', 'obsessed', 'massachusetts'],
     ['jokes', 'mil', 'dedicated'],
     ['feminist', 'generosity', 'homosexual'],
     ['home', 'calibrate', 'still'],
     ['sorrow', 'deep', 'wells']]



## NounProject


```python
import requests, json
from requests_oauthlib import OAuth1
from PIL import Image
import urllib.request
import os
```


```python
png_dir = 'NounProjectOutputs/png_images/'
jpg_dir = 'NounProjectOutputs/jpg_images/'
```


```python
auth = OAuth1("1aac7c276b39401f9f042c53e8f8e5d6", "38b8f9bf4a074812918528889a076fa1")

not_found = []
no_icon_url = []

for search_terms in top3:
    for search_term in search_terms:
        endpoint = "http://api.thenounproject.com/icon/" + search_term
        response = requests.get(endpoint, auth=auth)
        
        if(response.status_code==404):
            not_found.append(search_term)
            continue
            
        parsed_response = response.json()
        
        if 'preview_url' not in parsed_response['icon']:
            no_icon_url.append(search_term)
            continue
            
        icon_url = parsed_response['icon']['preview_url']
        urllib.request.urlretrieve(icon_url, png_dir + search_term + ".png")
```


```python
def png2jpg(image_path):
    image = Image.open('NounProjectOutputs/png_images/' + image_path).convert("RGBA")
    new_image = Image.new("RGBA", image.size, "WHITE")
    new_image.paste(image, (0, 0), image)
    new_image.convert('RGB').save(jpg_dir + image_path.split('.')[0] + '.jpg', "JPEG") 
```


```python
for pngFile in os.listdir('NounProjectOutputs/png_images/'):
    png2jpg(pngFile)
```

## Layout


```python
import math
from PIL import Image

def arrangeImagesInCircle(masterImage, imagesToArrange, radius):
    imgWidth, imgHeight = masterImage.size

#     diameter = min(
#         imgWidth  - max(img.size[0] for img in imagesToArrange),
#         imgHeight - max(img.size[1] for img in imagesToArrange)
#     )
#     radius = diameter / 2

    circleCenterX = imgWidth  / 2
    circleCenterY = imgHeight / 2
    theta = 2*math.pi / len(imagesToArrange)
    for i, curImg in enumerate(imagesToArrange):
        angle = i * theta
        dx = int(radius * math.cos(angle))
        dy = int(radius * math.sin(angle))

        pos = (
            int(circleCenterX + dx - curImg.size[0]/2),
            int(circleCenterY + dy - curImg.size[1]/2)
        )
        masterImage.paste(curImg, pos, mask=curImg)
```


```python
pngFilenames = [[png_dir + search_term + '.png' for search_term in search_terms if search_term not in not_found] for search_terms in top3]
```


```python
jpgFilenames = [[jpg_dir + search_term + '.jpg' for search_term in search_terms if search_term not in not_found] for search_terms in top3]
```


```python
for i in range(50):
    img = Image.new("RGB", (600,600), "WHITE")

    images = [Image.open(filename) for filename in pngFilenames[i]]
    arrangeImagesInCircle(img, images, 100)

    img.convert('RGB').save("EssenceOutputs/essence-" + str(i) + ".jpg", "JPEG")
```

## Detect Mood


```python
import pandas as pd
import numpy as np
from nltk.corpus import stopwords
import re
from sklearn import preprocessing
from sklearn.model_selection import train_test_split
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.feature_extraction.text import CountVectorizer
from sklearn.metrics import accuracy_score
from sklearn.naive_bayes import MultinomialNB
from sklearn.linear_model import SGDClassifier
from sklearn.linear_model import LogisticRegression
from sklearn.ensemble import RandomForestClassifier
```


```python
data = pd.read_csv('text_emotion.csv')

# sentiment_list = ['anger', 'boredom', 'empty', 'enthusiasm', 'fun', 'happiness', 
#                   'hate', 'love', 'neutral', 'relief', 'sadness', 'surprise', 'worry']

data = data.drop('author', axis=1)
data = data.drop(data[data.sentiment == 'boredom'].index)
data = data.drop(data[data.sentiment == 'empty'].index)
data = data.drop(data[data.sentiment == 'fun'].index)
data = data.drop(data[data.sentiment == 'relief'].index)
data = data.drop(data[data.sentiment == 'surprise'].index)

# Making all letters lowercase
data['content'] = data['content'].apply(lambda x: " ".join(x.lower() for x in x.split()))

# Removing Punctuation, Symbols
data['content'] = data['content'].str.replace('[^\w\s]',' ')

# Removing Stop Words using NLTK
stop = stopwords.words('english')
data['content'] = data['content'].apply(lambda x: " ".join(x for x in x.split() if x not in stop))

# #Lemmatisation
# data['content'] = data['content'].apply(lambda x: " ".join([Word(word).lemmatize() for word in x.split()]))
#Correcting Letter Repetitions

def de_repeat(text):
    pattern = re.compile(r"(.)\1{2,}")
    return pattern.sub(r"\1\1", text)

data['content'] = data['content'].apply(lambda x: " ".join(de_repeat(x) for x in x.split()))

# Code to find the top 10,000 rarest words appearing in the data
freq = pd.Series(' '.join(data['content']).split()).value_counts()[-10000:]

# Removing all those rarely appearing words from the data
freq = list(freq.index)
data['content'] = data['content'].apply(lambda x: " ".join(x for x in x.split() if x not in freq))

#Encoding output labels 'sadness' as '1' & 'happiness' as '0'
lbl_enc = preprocessing.LabelEncoder()
y = lbl_enc.fit_transform(data.sentiment.values)

# Splitting into training and testing data in 90:10 ratio
X_train, X_val, y_train, y_val = train_test_split(data.content.values, y, stratify=y, random_state=42, test_size=0.1, shuffle=True)

# Extracting TF-IDF parameters
# tfidf = TfidfVectorizer(max_features=1000, analyzer='word',ngram_range=(1,3))
# X_train_tfidf = tfidf.fit_transform(X_train)
# X_val_tfidf = tfidf.fit_transform(X_val)

# Extracting Count Vectors Parameters
count_vect = CountVectorizer(analyzer='word')
count_vect.fit(data['content'])
X_train_count =  count_vect.transform(X_train)
X_val_count =  count_vect.transform(X_val)
```


```python
list(enumerate(lbl_enc.classes_))
```




    [(0, 'anger'),
     (1, 'enthusiasm'),
     (2, 'happiness'),
     (3, 'hate'),
     (4, 'love'),
     (5, 'neutral'),
     (6, 'sadness'),
     (7, 'worry')]




```python
# Model 1: Linear SVM
lsvm = SGDClassifier(alpha=0.001, random_state=5, max_iter=15, tol=None)
lsvm.fit(X_train_count, y_train)
y_pred = lsvm.predict(X_val_count)
print('lsvm using count vectors accuracy %s' % accuracy_score(y_pred, y_val))

# Model 2: Logistic Regression
logreg = LogisticRegression(C=1)
logreg.fit(X_train_count, y_train)
y_pred = logreg.predict(X_val_count)
print('log reg count vectors accuracy %s' % accuracy_score(y_pred, y_val))
```

    lsvm using count vectors accuracy 0.41032527603700386


    //anaconda3/envs/cs231n/lib/python3.7/site-packages/sklearn/linear_model/logistic.py:432: FutureWarning: Default solver will be changed to 'lbfgs' in 0.22. Specify a solver to silence this warning.
      FutureWarning)
    //anaconda3/envs/cs231n/lib/python3.7/site-packages/sklearn/linear_model/logistic.py:469: FutureWarning: Default multi_class will be changed to 'auto' in 0.22. Specify the multi_class option to silence this warning.
      "this warning.", FutureWarning)


    log reg count vectors accuracy 0.40704267382870785



```python
desc_count_vectors = count_vect.transform(descriptors)

desc_emotion_pred = lsvm.predict(desc_count_vectors)
print(desc_emotion_pred)
```

    [4 4 5 4 7 7 2 2 7 7 4 5 4 5 5 2 4 4 6 7 4 2 2 4 4 7 7 4 7 4 4 4 4 2 2 7 4
     4 4 4 4 4 2 4 5 4 5 4 4 2]

