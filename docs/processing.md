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
data = data.drop(data[data.sentiment == 'sadness'].index)
data = data.drop(data[data.sentiment == 'fun'].index)
data = data.drop(data[data.sentiment == 'enthusiasm'].index)

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
     (1, 'happiness'),
     (2, 'hate'),
     (3, 'love'),
     (4, 'neutral'),
     (5, 'worry')]




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

    lsvm using count vectors accuracy 0.5070677781805002

    log reg count vectors accuracy 0.501268575570859



```python
desc_count_vectors = count_vect.transform(descriptors)

desc_emotion_pred = lsvm.predict(desc_count_vectors)
print(desc_emotion_pred)
```

    [3 3 4 3 5 5 4 1 5 3 3 4 3 4 4 1 3 5 5 5 3 1 1 1 3 5 5 3 5 3 3 3 3 5 1 5 3
     3 3 3 3 3 1 3 5 3 4 3 3 1]



```python
from IPython.display import Image, display, HTML
```


```python
desc_emotions = []
k = 0
for i in desc_array:
    desc_emotions.append((i, lbl_enc.classes_[desc_emotion_pred[k]]))
    k += 1
```


```python
desc_emotions
```




    [(['Person 1',
       'I am a 28-year-old woman living in Massachusetts.',
       "I'm neurotic and eccentric but good at heart.",
       'I am obsessed with rabbits and love technology.'],
      'love'),
     (['Person 2',
       'I am dedicated and persistent and willing to go the extra mil',
       "'m fun loving and like to make people laugh by telling jokes and making light of situations",
       'I am insightful and am able to fit together pieces to understand the big pictur'],
      'love'),
     (['Person 3',
       'I am a feminist, a student, and a homosexual.',
       'I am kind, nurturing, caring, and genuine.',
       'My honesty, my loyalty, and my generosity make me me.'],
      'neutral'),
     (['Person 4',
       "I'm an immigrant who became a citizen of the United States. I'm an American.",
       "I can be stubborn and stand-offish, but I still care very much about my friends and family. I'm a nerd about movies/tvshows/books. I love video games and prefer to stay home.",
       "I'm introverted, so I need time alone to recharge and recalibrate."],
      'love'),
     (['Person 5',
       "I'm a boring person",
       "I'm quiet and introspective.",
       'I have deep wells of sorrow.'],
      'worry'),
     (['Person 6',
       'I am a girl who lives in New York City in my twenties who is incredibly close with my family.',
       'I am very social and outgoing.',
       'I am outgoing and care tremendously about my friends.'],
      'worry'),
     (['Person 7',
       'I am a mom of 3',
       'I like R &B Music, Japanese Food, Pizz',
       'I am sympathetic.'],
      'neutral'),
     (['Person 8',
       'I am a licensed counselor.',
       "I'm silly and funny.",
       "I'm fun and sarcastic a lot of the time."],
      'happiness'),
     (['Person 9',
       "I'm Jim, a 53 year old american man",
       "I'm forceful, happy, calm and occasionally grumpy with a touch of sarcasm.",
       "I'm a drivan dominant at work and play. My wife is essential to my life. I'd be lost without her grounding me."],
      'worry'),
     (['Person 10',
       "I'm a fat, biracial bisexual woman.",
       "I'm a funny depressive--aren't all depressives a riot?",
       "I'm a boring drudge, not glamorous or fancy, but fairly dependable."],
      'love'),
     (['Person 11',
       'I am an adventurous geeky skydiv',
       'I am fun-loving and love life.',
       'I am intelligent and caring.'],
      'love'),
     (['Person 12',
       "I am a person who believes that honesty and integrity is very important in today's society and world.",
       'I am a person who is warm and sensitive to the feelings of others.',
       'I see myself as one who you can count when the chips are down.'],
      'neutral'),
     (['Person 13',
       "I am shy from those whom I don't know yet energetic and caring to those whom I do know.",
       'I am a very happy and appreciate all life equally.',
       'God is an important part of who I am. He allows me to me loving to all creatures no matter how small.'],
      'love'),
     (['Person 14',
       'I am a human',
       'I am curious and interested in urban',
       'My passion for cities and cultur'],
      'neutral'),
     (['Person 15',
       'I am a musician',
       'm very laidback, easy going and unbrainwashed.',
       'Making music makes me tick.'],
      'neutral'),
     (['Person 16',
       'I am a middle aged woman.',
       'I am easy-going, caring, and nurturing.',
       "My essence is that I care a great deal about others to the point that I don't take care of myself."],
      'happiness'),
     (['Person 17',
       'A male human being with a kind and loving personality.',
       'Video Games and food',
       'Humble, Kind, Loving'],
      'love'),
     (['Person 18',
       'I am a mother, wife, and friend',
       'I am like the shoulder you can cry on, or a listening ear.',
       'My family makes me me!'],
      'worry'),
     (['Person 19',
       'I am an "older" adult who is finally understanding what is important and not important in this life.',
       'I am an outgoing, sensitive, fun, creative and active person.',
       "Family is the essence of what makes me me. Without them, I'd be at a total loss."],
      'worry'),
     (['Person 20',
       "I'm a 30 year old married man with a 2 year old daughter.",
       "I'm hard working, determined, goal oriented, relaxed and down to earth.",
       'My ability to get along well with almost anyone is what makes me Me.'],
      'worry'),
     (['Person 21',
       'I am an untraditional college student who is employed full time.',
       "I am an agreeable person who doesn't like to be bothered with others.",
       'I am an introvert who is happy to pass the time by myself.'],
      'love'),
     (['Person 22',
       'A courteous femal',
       'Friendly and full of energy.',
       'Family is making me to smile and be happy.'],
      'happiness'),
     (['Person 23',
       'A 52 year old married woman',
       'Fun, outgoing, and social.',
       'I am always willing to lend a hand or give a listening ear.'],
      'happiness'),
     (['Person 24',
       'I am a 25 year old American woman',
       'I am introverted but also very nice and like to learn',
       'I try to make other people around me happy and try to make the world a better place to liv'],
      'happiness'),
     (['Person 25',
       'I am a mom and a wife.',
       'I am pretty boring and quiet.',
       'My love for my husband.'],
      'love'),
     (['Person 26',
       '28 year old mal',
       'ntellegent and s',
       'like to think about everything'],
      'worry'),
     (['Person 27',
       'n inquisitive person',
       'friendly and approachab',
       'desire to always learn new thing'],
      'worry'),
     (['Person 28',
       'I am donald, I am a 25 year old married man, working full time as a social media manager.',
       'I am a friendly person, I like the outdoors, and going on adventures with my friends and family.',
       'I am warm hearted individual, I am very kind, I love everyone and try never to judge anyone, I put others before myself.'],
      'love'),
     (['Person 29',
       "I'm an average guy. A father, husband, brother, employee and friend. I am much like any other guy.",
       "I'm pretty down to earth. I like to laugh and play video games but I can be serious when I need to be serious.",
       'I think what makes me me is that I am very open-minded as a person. I believe in forming my own opinions rather than just taking things at face value. I like to learn and experience things rather than be told how things are.'],
      'worry'),
     (['Person 30',
       "I'm a man who loves his wife very much.",
       "I'm loyal, devoted and always trying to do best in order to support our family.",
       'Faith and strong will to pursue my hopes and dreams makes me to push through the day.'],
      'love'),
     (['Person 31',
       'I am a 43 old mother of two young boys under 7. I am am only child. I will be married for 9years in june.',
       'I am an honest person. I am very disorganized and tend to be a half full person. I am loyal.',
       'I have been created by God and uniquely created . My life experiences have made me me.'],
      'love'),
     (['Person 32',
       'I am a woman, a wife, a mother of 4.',
       'I am introverted, quiet, compassionate, impractical, prone to depression.',
       'I love to write.'],
      'love'),
     (['Person 33',
       "I'm a wife and mother of 5 children.",
       'I am introverted, honest and generous.',
       'My Catholic faith is a big part of who I am and how I live my life.'],
      'love'),
     (['Person 34',
       'im a strong independent person.',
       'm kind and warm hearted.',
       'persoanility makes me who i am.'],
      'worry'),
     (['Person 35',
       "I'm a mom of 3 children.",
       'I am an outgoing, fun person who likes to go out and be social.',
       'I am sincere, honest, and a good friend.  I am caring to others, especially my close friends!'],
      'happiness'),
     (['Person 36',
       'Someone who is calm, peaceful and stays relaxed under pressure.',
       'I am nice, kind and funny but usually quiet.',
       'I am caring, and I feel the need to help others.'],
      'worry'),
     (['Person 37', "I'm a loving and caring mom.", 'Fun, original, happ', 'M'],
      'love'),
     (['Person 38',
       'I am a teacher of ESL',
       'I love my husband and our dog, and want to be a mom, even though we are currently struggling with a miscarriage after 2 years of infertility treatments.',
       'Right now, humor and talking to my friends in my infertility support group, as well as hanging out and taking pictures of my dog and husband.'],
      'love'),
     (['Person 39',
       "I'm a cat lover who's kind of weird, but smart and funny.",
       "I'm relaxed and love animals.",
       'I have kind of a weird take on things.'],
      'love'),
     (['Person 40',
       'i am a hard working smart femal',
       'm funny yet clever and warm',
       'love for animals and other'],
      'love'),
     (['Person 41',
       "I'm just a nice guy trying to be loving to others and find his way in the world.",
       "I'm nerdy, intelligent, and funny.",
       "I'm nobody special, but I do value my individuality and I love artistic expression."],
      'love'),
     (['Person 42',
       'I am a wife, mother, and college student.',
       'I am a loving, smart, fun, caring person . I love to sing, write, do crafts, art and whatever else I can do to help uplift others.',
       'My personality and humor. But more importantly my big heart.'],
      'love'),
     (['Person 43',
       'I am funny.',
       'I am easy going.',
       'I have a great personality.'],
      'happiness'),
     (['Person 44',
       'nry johnson',
       'stern,friendly,loving,strong of mind,family oriented,good worker,always looking forward within memories of the pas',
       'loving all the members of my faily,past and pr'],
      'love'),
     (['Person 45',
       'I am a daughter, sister, friend, and advocat',
       "I advocate for those who don't have a voic",
       'I care so deeply about children involved in the system and I will do almost anything to help them!'],
      'worry'),
     (['Person 46',
       'I am a mom, wife, educator, sister, and daughter.',
       "I'm an introverted extrovert. I love to be on stage and the center of attention, but I hate small talk.",
       'I am my own unique person who has never been known to follow a crowd.'],
      'love'),
     (['Person 47',
       'I am a mother, friend, and wif',
       'I am active, adventurous, and hardwarling.',
       'My values and principals.'],
      'neutral'),
     (['Person 48',
       'I am a soul that currently has the role of wife, mother, daughter, sister, and friend.',
       "I'm an introspective, introverted individual who cherishes both family time and alone time.",
       'My quick wit, warm smile, and love of laughter make me who I am.'],
      'love'),
     (['Person 49',
       'I am a working mom.',
       'I am calm, determined, and loving.',
       'The essence of what makes me is my compassion and caring.'],
      'love'),
     (['Person 50',
       'I am a 27 year old special education teacher who lives in California.',
       'I am a sociable and very goofy young guy who likes to make everyone laugh.',
       'The essence of what makes me myself is that I am always generally positive and like to spread a smile to all those around me!'],
      'happiness')]
