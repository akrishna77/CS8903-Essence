---
layout: page
title: Paintings
---

Retrieving relevant paintings based on emotion of the answer.

```python
moods = ['anger', 'anticipation', 'disgust', 'fear', 'joy', 'negative', 'positive', 'sadness', 'surprise', 'trust']
final_emotions
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
      <th>anger</th>
      <th>anticipation</th>
      <th>disgust</th>
      <th>fear</th>
      <th>joy</th>
      <th>negative</th>
      <th>positive</th>
      <th>sadness</th>
      <th>surprise</th>
      <th>trust</th>
    </tr>
    <tr>
      <th>0</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>abacus</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>abandon</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>abandoned</th>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>abandonment</th>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>abba</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>abbot</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>abduction</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>aberrant</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>aberration</th>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>abhor</th>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>abhorrent</th>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>ability</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>abject</th>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>abnormal</th>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>abolish</th>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>abolition</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>abominable</th>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>abomination</th>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>abort</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>abortion</th>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>abortive</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>abovementioned</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>abrasion</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>abrogate</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>abrupt</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>abscess</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>absence</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>absent</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>absentee</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>absenteeism</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>wreck</th>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>wrecked</th>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>wrench</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>wrestling</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>wretch</th>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>wretched</th>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>wring</th>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>wrinkled</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>writer</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>wrong</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>wrongdoing</th>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>wrongful</th>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>wrongly</th>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>wrought</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>wry</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>xenophobia</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>yawn</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>yawning</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>yearning</th>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>yell</th>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>yellows</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>yelp</th>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>young</th>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>younger</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>youth</th>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>zany</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>zeal</th>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>zealous</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>zest</th>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>zip</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>6468 rows × 10 columns</p>
</div>





```python
paintings = pd.read_csv('WikiArt-Emotions/WikiArt-Emotions-All.tsv', delimiter='\t')
filter_col = ['Image URL', 'Art (image+title): anger', 'Art (image+title): anticipation', 'Art (image+title): disgust', 'Art (image+title): fear', 'Art (image+title): happiness', 'Art (image+title): pessimism', 'Art (image+title): optimism', 'Art (image+title): sadness', 'Art (image+title): surprise', 'Art (image+title): trust']
filtered_paintings = paintings[filter_col]
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
      <th>Image URL</th>
      <th>Art (image+title): anger</th>
      <th>Art (image+title): anticipation</th>
      <th>Art (image+title): disgust</th>
      <th>Art (image+title): fear</th>
      <th>Art (image+title): happiness</th>
      <th>Art (image+title): pessimism</th>
      <th>Art (image+title): optimism</th>
      <th>Art (image+title): sadness</th>
      <th>Art (image+title): surprise</th>
      <th>Art (image+title): trust</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>https://use2-uploads3.wikiart.org/00123/images...</td>
      <td>0.012</td>
      <td>0.071</td>
      <td>0.000</td>
      <td>0.036</td>
      <td>0.750</td>
      <td>0.048</td>
      <td>0.333</td>
      <td>0.131</td>
      <td>0.048</td>
      <td>0.274</td>
    </tr>
    <tr>
      <th>1</th>
      <td>https://use2-uploads1.wikiart.org/images/keith...</td>
      <td>0.000</td>
      <td>0.500</td>
      <td>0.100</td>
      <td>0.300</td>
      <td>0.100</td>
      <td>0.200</td>
      <td>0.100</td>
      <td>0.100</td>
      <td>0.500</td>
      <td>0.100</td>
    </tr>
    <tr>
      <th>2</th>
      <td>https://use2-uploads3.wikiart.org/images/j-zse...</td>
      <td>0.000</td>
      <td>0.200</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.500</td>
      <td>0.000</td>
      <td>0.300</td>
      <td>0.000</td>
      <td>0.100</td>
      <td>0.300</td>
    </tr>
    <tr>
      <th>3</th>
      <td>https://use2-uploads2.wikiart.org/00124/images...</td>
      <td>0.000</td>
      <td>0.091</td>
      <td>0.091</td>
      <td>0.091</td>
      <td>0.091</td>
      <td>0.091</td>
      <td>0.091</td>
      <td>0.273</td>
      <td>0.182</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>https://use2-uploads6.wikiart.org/images/david...</td>
      <td>0.231</td>
      <td>0.154</td>
      <td>0.231</td>
      <td>0.308</td>
      <td>0.154</td>
      <td>0.154</td>
      <td>0.231</td>
      <td>0.231</td>
      <td>0.077</td>
      <td>0.538</td>
    </tr>
    <tr>
      <th>5</th>
      <td>https://use2-uploads4.wikiart.org/images/lyone...</td>
      <td>0.000</td>
      <td>0.134</td>
      <td>0.030</td>
      <td>0.134</td>
      <td>0.358</td>
      <td>0.104</td>
      <td>0.134</td>
      <td>0.090</td>
      <td>0.224</td>
      <td>0.090</td>
    </tr>
    <tr>
      <th>6</th>
      <td>https://use2-uploads1.wikiart.org/images/nikol...</td>
      <td>0.000</td>
      <td>0.100</td>
      <td>0.000</td>
      <td>0.600</td>
      <td>0.100</td>
      <td>0.100</td>
      <td>0.000</td>
      <td>0.300</td>
      <td>0.000</td>
      <td>0.100</td>
    </tr>
    <tr>
      <th>7</th>
      <td>https://use2-uploads7.wikiart.org/images/charl...</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.700</td>
      <td>0.100</td>
      <td>0.400</td>
      <td>0.100</td>
      <td>0.000</td>
      <td>0.200</td>
    </tr>
    <tr>
      <th>8</th>
      <td>https://use2-uploads7.wikiart.org/images/rober...</td>
      <td>0.000</td>
      <td>0.417</td>
      <td>0.083</td>
      <td>0.083</td>
      <td>0.000</td>
      <td>0.083</td>
      <td>0.000</td>
      <td>0.167</td>
      <td>0.500</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>9</th>
      <td>https://use2-uploads7.wikiart.org/images/richa...</td>
      <td>0.000</td>
      <td>0.100</td>
      <td>0.200</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.100</td>
      <td>0.400</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>10</th>
      <td>https://use2-uploads8.wikiart.org/images/patri...</td>
      <td>0.000</td>
      <td>0.091</td>
      <td>0.091</td>
      <td>0.000</td>
      <td>0.636</td>
      <td>0.000</td>
      <td>0.182</td>
      <td>0.000</td>
      <td>0.091</td>
      <td>0.182</td>
    </tr>
    <tr>
      <th>11</th>
      <td>https://use2-uploads0.wikiart.org/images/georg...</td>
      <td>0.000</td>
      <td>0.200</td>
      <td>0.100</td>
      <td>0.000</td>
      <td>0.200</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.400</td>
      <td>0.100</td>
      <td>0.900</td>
    </tr>
    <tr>
      <th>12</th>
      <td>https://use2-uploads4.wikiart.org/images/ron-g...</td>
      <td>0.000</td>
      <td>0.182</td>
      <td>0.182</td>
      <td>0.000</td>
      <td>0.091</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.273</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>13</th>
      <td>https://use2-uploads0.wikiart.org/images/louis...</td>
      <td>0.000</td>
      <td>0.400</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.200</td>
      <td>0.100</td>
      <td>0.400</td>
      <td>0.100</td>
    </tr>
    <tr>
      <th>14</th>
      <td>https://use2-uploads2.wikiart.org/images/franc...</td>
      <td>0.000</td>
      <td>0.167</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.333</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.583</td>
      <td>0.083</td>
    </tr>
    <tr>
      <th>15</th>
      <td>https://use2-uploads6.wikiart.org/images/domen...</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.083</td>
      <td>0.083</td>
      <td>0.167</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.083</td>
      <td>0.083</td>
      <td>0.500</td>
    </tr>
    <tr>
      <th>16</th>
      <td>https://use2-uploads6.wikiart.org/images/jacqu...</td>
      <td>0.000</td>
      <td>0.200</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.300</td>
      <td>0.000</td>
      <td>0.100</td>
      <td>0.000</td>
      <td>0.100</td>
      <td>0.800</td>
    </tr>
    <tr>
      <th>17</th>
      <td>https://use2-uploads7.wikiart.org/images/karl-...</td>
      <td>0.000</td>
      <td>0.500</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.200</td>
      <td>0.000</td>
      <td>0.200</td>
      <td>0.700</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>18</th>
      <td>https://use2-uploads2.wikiart.org/images/edvar...</td>
      <td>0.000</td>
      <td>0.091</td>
      <td>0.091</td>
      <td>0.273</td>
      <td>0.000</td>
      <td>0.182</td>
      <td>0.000</td>
      <td>0.727</td>
      <td>0.091</td>
      <td>0.182</td>
    </tr>
    <tr>
      <th>19</th>
      <td>https://use2-uploads4.wikiart.org/images/herbe...</td>
      <td>0.000</td>
      <td>0.300</td>
      <td>0.100</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.100</td>
      <td>0.100</td>
      <td>0.300</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>20</th>
      <td>https://use2-uploads2.wikiart.org/images/joan-...</td>
      <td>0.091</td>
      <td>0.364</td>
      <td>0.091</td>
      <td>0.364</td>
      <td>0.000</td>
      <td>0.273</td>
      <td>0.000</td>
      <td>0.273</td>
      <td>0.182</td>
      <td>0.182</td>
    </tr>
    <tr>
      <th>21</th>
      <td>https://use2-uploads3.wikiart.org/images/adria...</td>
      <td>0.027</td>
      <td>0.161</td>
      <td>0.027</td>
      <td>0.036</td>
      <td>0.518</td>
      <td>0.009</td>
      <td>0.232</td>
      <td>0.027</td>
      <td>0.098</td>
      <td>0.348</td>
    </tr>
    <tr>
      <th>22</th>
      <td>https://use2-uploads4.wikiart.org/images/honor...</td>
      <td>0.000</td>
      <td>0.154</td>
      <td>0.000</td>
      <td>0.154</td>
      <td>0.538</td>
      <td>0.154</td>
      <td>0.154</td>
      <td>0.231</td>
      <td>0.077</td>
      <td>0.231</td>
    </tr>
    <tr>
      <th>23</th>
      <td>https://use2-uploads5.wikiart.org/images/victo...</td>
      <td>0.000</td>
      <td>0.583</td>
      <td>0.000</td>
      <td>0.083</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.167</td>
      <td>0.000</td>
      <td>0.417</td>
      <td>0.083</td>
    </tr>
    <tr>
      <th>24</th>
      <td>https://use2-uploads1.wikiart.org/images/anton...</td>
      <td>0.091</td>
      <td>0.000</td>
      <td>0.273</td>
      <td>0.545</td>
      <td>0.000</td>
      <td>0.091</td>
      <td>0.000</td>
      <td>0.091</td>
      <td>0.455</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>25</th>
      <td>https://use2-uploads1.wikiart.org/images/corne...</td>
      <td>0.000</td>
      <td>0.364</td>
      <td>0.273</td>
      <td>0.091</td>
      <td>0.091</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.091</td>
      <td>0.636</td>
      <td>0.182</td>
    </tr>
    <tr>
      <th>26</th>
      <td>https://use2-uploads4.wikiart.org/images/anton...</td>
      <td>0.000</td>
      <td>0.400</td>
      <td>0.200</td>
      <td>0.000</td>
      <td>0.300</td>
      <td>0.000</td>
      <td>0.100</td>
      <td>0.100</td>
      <td>0.100</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>27</th>
      <td>https://use2-uploads8.wikiart.org/images/afro/...</td>
      <td>0.000</td>
      <td>0.300</td>
      <td>0.300</td>
      <td>0.200</td>
      <td>0.000</td>
      <td>0.100</td>
      <td>0.000</td>
      <td>0.300</td>
      <td>0.800</td>
      <td>0.100</td>
    </tr>
    <tr>
      <th>28</th>
      <td>https://use2-uploads6.wikiart.org/images/eilee...</td>
      <td>0.055</td>
      <td>0.218</td>
      <td>0.145</td>
      <td>0.236</td>
      <td>0.055</td>
      <td>0.000</td>
      <td>0.073</td>
      <td>0.073</td>
      <td>0.327</td>
      <td>0.073</td>
    </tr>
    <tr>
      <th>29</th>
      <td>https://use2-uploads1.wikiart.org/images/lynda...</td>
      <td>0.000</td>
      <td>0.500</td>
      <td>0.200</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.500</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>4075</th>
      <td>https://use2-uploads6.wikiart.org/images/serge...</td>
      <td>0.000</td>
      <td>0.500</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.300</td>
      <td>0.000</td>
      <td>0.200</td>
      <td>0.000</td>
      <td>0.600</td>
      <td>0.100</td>
    </tr>
    <tr>
      <th>4076</th>
      <td>https://use2-uploads4.wikiart.org/images/dosso...</td>
      <td>0.000</td>
      <td>0.100</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.400</td>
      <td>0.000</td>
      <td>0.100</td>
      <td>0.200</td>
      <td>0.000</td>
      <td>0.300</td>
    </tr>
    <tr>
      <th>4077</th>
      <td>https://use2-uploads4.wikiart.org/images/andre...</td>
      <td>0.131</td>
      <td>0.180</td>
      <td>0.115</td>
      <td>0.361</td>
      <td>0.049</td>
      <td>0.082</td>
      <td>0.033</td>
      <td>0.197</td>
      <td>0.311</td>
      <td>0.131</td>
    </tr>
    <tr>
      <th>4078</th>
      <td>https://use2-uploads2.wikiart.org/images/o-lou...</td>
      <td>0.000</td>
      <td>0.400</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.500</td>
      <td>0.000</td>
      <td>0.400</td>
      <td>0.300</td>
      <td>0.100</td>
      <td>0.200</td>
    </tr>
    <tr>
      <th>4079</th>
      <td>https://use2-uploads2.wikiart.org/images/jock-...</td>
      <td>0.000</td>
      <td>0.200</td>
      <td>0.100</td>
      <td>0.000</td>
      <td>0.500</td>
      <td>0.000</td>
      <td>0.300</td>
      <td>0.000</td>
      <td>0.500</td>
      <td>0.100</td>
    </tr>
    <tr>
      <th>4080</th>
      <td>https://use2-uploads1.wikiart.org/images/edwar...</td>
      <td>0.000</td>
      <td>0.100</td>
      <td>0.300</td>
      <td>0.100</td>
      <td>0.100</td>
      <td>0.000</td>
      <td>0.100</td>
      <td>0.100</td>
      <td>0.100</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>4081</th>
      <td>https://use2-uploads0.wikiart.org/images/henri...</td>
      <td>0.000</td>
      <td>0.100</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.400</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.100</td>
      <td>0.100</td>
      <td>0.100</td>
    </tr>
    <tr>
      <th>4082</th>
      <td>https://use2-uploads6.wikiart.org/images/herve...</td>
      <td>0.000</td>
      <td>0.200</td>
      <td>0.200</td>
      <td>0.000</td>
      <td>0.400</td>
      <td>0.000</td>
      <td>0.200</td>
      <td>0.000</td>
      <td>0.300</td>
      <td>0.100</td>
    </tr>
    <tr>
      <th>4083</th>
      <td>https://use2-uploads5.wikiart.org/images/pat-l...</td>
      <td>0.091</td>
      <td>0.091</td>
      <td>0.091</td>
      <td>0.000</td>
      <td>0.182</td>
      <td>0.000</td>
      <td>0.364</td>
      <td>0.000</td>
      <td>0.182</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>4084</th>
      <td>https://use2-uploads3.wikiart.org/00115/images...</td>
      <td>0.000</td>
      <td>0.100</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.500</td>
      <td>0.000</td>
      <td>0.100</td>
      <td>0.000</td>
      <td>0.100</td>
      <td>0.500</td>
    </tr>
    <tr>
      <th>4085</th>
      <td>https://use2-uploads6.wikiart.org/images/jo-ba...</td>
      <td>0.000</td>
      <td>0.400</td>
      <td>0.200</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.300</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>4086</th>
      <td>https://use2-uploads7.wikiart.org/images/olivi...</td>
      <td>0.000</td>
      <td>0.250</td>
      <td>0.167</td>
      <td>0.083</td>
      <td>0.083</td>
      <td>0.000</td>
      <td>0.250</td>
      <td>0.083</td>
      <td>0.250</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>4087</th>
      <td>https://use2-uploads1.wikiart.org/images/jean-...</td>
      <td>0.000</td>
      <td>0.100</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.900</td>
      <td>0.000</td>
      <td>0.200</td>
      <td>0.000</td>
      <td>0.100</td>
      <td>0.500</td>
    </tr>
    <tr>
      <th>4088</th>
      <td>https://use2-uploads3.wikiart.org/00144/images...</td>
      <td>0.000</td>
      <td>0.075</td>
      <td>0.000</td>
      <td>0.025</td>
      <td>0.250</td>
      <td>0.000</td>
      <td>0.138</td>
      <td>0.075</td>
      <td>0.037</td>
      <td>0.287</td>
    </tr>
    <tr>
      <th>4089</th>
      <td>https://use2-uploads2.wikiart.org/00150/images...</td>
      <td>0.000</td>
      <td>0.500</td>
      <td>0.100</td>
      <td>0.100</td>
      <td>0.000</td>
      <td>0.200</td>
      <td>0.100</td>
      <td>0.000</td>
      <td>0.400</td>
      <td>0.300</td>
    </tr>
    <tr>
      <th>4090</th>
      <td>https://use2-uploads2.wikiart.org/images/kazuo...</td>
      <td>0.000</td>
      <td>0.200</td>
      <td>0.100</td>
      <td>0.100</td>
      <td>0.500</td>
      <td>0.000</td>
      <td>0.100</td>
      <td>0.000</td>
      <td>0.200</td>
      <td>0.200</td>
    </tr>
    <tr>
      <th>4091</th>
      <td>https://use2-uploads0.wikiart.org/images/david...</td>
      <td>0.000</td>
      <td>0.500</td>
      <td>0.000</td>
      <td>0.083</td>
      <td>0.167</td>
      <td>0.000</td>
      <td>0.083</td>
      <td>0.000</td>
      <td>0.500</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>4092</th>
      <td>https://use2-uploads2.wikiart.org/images/piet-...</td>
      <td>0.000</td>
      <td>0.154</td>
      <td>0.000</td>
      <td>0.077</td>
      <td>0.385</td>
      <td>0.000</td>
      <td>0.231</td>
      <td>0.154</td>
      <td>0.231</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>4093</th>
      <td>https://use2-uploads4.wikiart.org/images/rogie...</td>
      <td>0.100</td>
      <td>0.300</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.300</td>
      <td>0.100</td>
      <td>0.300</td>
      <td>0.200</td>
      <td>0.100</td>
      <td>0.200</td>
    </tr>
    <tr>
      <th>4094</th>
      <td>https://use2-uploads6.wikiart.org/images/steph...</td>
      <td>0.016</td>
      <td>0.281</td>
      <td>0.047</td>
      <td>0.063</td>
      <td>0.328</td>
      <td>0.000</td>
      <td>0.219</td>
      <td>0.016</td>
      <td>0.359</td>
      <td>0.094</td>
    </tr>
    <tr>
      <th>4095</th>
      <td>https://use2-uploads5.wikiart.org/images/johan...</td>
      <td>0.455</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.091</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.545</td>
    </tr>
    <tr>
      <th>4096</th>
      <td>https://use2-uploads5.wikiart.org/images/paolo...</td>
      <td>0.039</td>
      <td>0.078</td>
      <td>0.052</td>
      <td>0.091</td>
      <td>0.208</td>
      <td>0.026</td>
      <td>0.338</td>
      <td>0.000</td>
      <td>0.065</td>
      <td>0.481</td>
    </tr>
    <tr>
      <th>4097</th>
      <td>https://use2-uploads7.wikiart.org/images/richa...</td>
      <td>0.000</td>
      <td>0.167</td>
      <td>0.083</td>
      <td>0.000</td>
      <td>0.083</td>
      <td>0.000</td>
      <td>0.167</td>
      <td>0.000</td>
      <td>0.583</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>4098</th>
      <td>https://use2-uploads7.wikiart.org/images/max-p...</td>
      <td>0.000</td>
      <td>0.100</td>
      <td>0.100</td>
      <td>0.000</td>
      <td>0.800</td>
      <td>0.000</td>
      <td>0.300</td>
      <td>0.000</td>
      <td>0.100</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>4099</th>
      <td>https://use2-uploads3.wikiart.org/images/giorg...</td>
      <td>0.000</td>
      <td>0.083</td>
      <td>0.333</td>
      <td>0.167</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.167</td>
      <td>0.250</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>4100</th>
      <td>https://use2-uploads7.wikiart.org/images/ruppr...</td>
      <td>0.000</td>
      <td>0.273</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.091</td>
      <td>0.091</td>
      <td>0.273</td>
      <td>0.091</td>
      <td>0.091</td>
      <td>0.091</td>
    </tr>
    <tr>
      <th>4101</th>
      <td>https://use2-uploads4.wikiart.org/images/oscar...</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.300</td>
      <td>0.600</td>
      <td>0.000</td>
      <td>0.100</td>
      <td>0.000</td>
      <td>0.100</td>
      <td>0.100</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>4102</th>
      <td>https://use2-uploads2.wikiart.org/images/georg...</td>
      <td>0.000</td>
      <td>0.231</td>
      <td>0.154</td>
      <td>0.154</td>
      <td>0.154</td>
      <td>0.154</td>
      <td>0.154</td>
      <td>0.154</td>
      <td>0.154</td>
      <td>0.077</td>
    </tr>
    <tr>
      <th>4103</th>
      <td>https://use2-uploads0.wikiart.org/images/marie...</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.000</td>
      <td>0.083</td>
      <td>0.583</td>
      <td>0.000</td>
      <td>0.167</td>
      <td>0.083</td>
      <td>0.250</td>
      <td>0.250</td>
    </tr>
    <tr>
      <th>4104</th>
      <td>https://use2-uploads4.wikiart.org/images/paula...</td>
      <td>0.021</td>
      <td>0.149</td>
      <td>0.000</td>
      <td>0.128</td>
      <td>0.426</td>
      <td>0.043</td>
      <td>0.170</td>
      <td>0.043</td>
      <td>0.085</td>
      <td>0.085</td>
    </tr>
  </tbody>
</table>
<p>4105 rows × 11 columns</p>
</div>




```python
from sklearn.neighbors import NearestNeighbors

nn = NearestNeighbors(1).fit(all_paintings)
dists, idxs = nn.kneighbors(person3.reshape(1,10))
filtered_paintings.iloc[idxs[0][0]]
```




    Art (image+title): anger           0.1
    Art (image+title): anticipation    0.1
    Art (image+title): disgust         0.0
    Art (image+title): fear            0.0
    Art (image+title): happiness       0.6
    Art (image+title): pessimism       0.0
    Art (image+title): optimism        0.6
    Art (image+title): sadness         0.0
    Art (image+title): surprise        0.1
    Art (image+title): trust           0.8
    Name: https://use2-uploads7.wikiart.org/images/eduardo-arroyo/winston-churchill-1970.jpg, dtype: float64


<img src="https://use2-uploads7.wikiart.org/images/eduardo-arroyo/winston-churchill-1970.jpg"/>


## Results after Style Transfer

    ['I am a feminist, a student, and a homosexual.', 'I am kind, nurturing, caring, and genuine.', ' My honesty, my loyalty, and my generosity make me me.']
    ['feminist', 'genuine', 'generosity']



<table><tr><td><img src='../EssenceOutputs/essence-2.jpg'></td><td><img src='../style/essence-2-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-2.png'></td><td></td></tr></table>


    ["I'm a boring person", "I'm quiet and introspective.", ' I have deep wells of sorrow.']
    ['boring', 'introspective', 'sorrow']



<table><tr><td><img src='../EssenceOutputs/essence-4.jpg'></td><td><img src='../style/essence-4-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-4.png'></td><td></td></tr></table>


    ['I am a licensed counselor.', "I'm silly and funny.", " I'm fun and sarcastic a lot of the time."]
    ['licensed', 'silly', 'sarcastic']



<table><tr><td><img src='../EssenceOutputs/essence-7.jpg'></td><td><img src='../style/essence-7-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-7.png'></td><td></td></tr></table>


    ["I'm Jim, a 53 year old american man", "I'm forceful, happy, calm and occasionally grumpy with a touch of sarcasm.", " I'm a drivan dominant at work and play. My wife is essential to my life. I'd be lost without her grounding me."]
    ['american', 'forceful', 'dominant']



<table><tr><td><img src='../EssenceOutputs/essence-8.jpg'></td><td><img src='../style/essence-8-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-8.png'></td><td></td></tr></table>


    ["I'm a fat, biracial bisexual woman.", "I'm a funny depressive--aren't all depressives a riot?", " I'm a boring drudge, not glamorous or fancy, but fairly dependable."]
    ['biracial', 'riot', 'drudge']



<table><tr><td><img src='../EssenceOutputs/essence-9.jpg'></td><td><img src='../style/essence-9-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-9.png'></td><td></td></tr></table>


    ['I am an adventurous geeky skydiver', 'I am fun-loving and love life.', ' I am intelligent and caring.']
    ['skydiver', 'life', 'intelligent']



<table><tr><td><img src='../EssenceOutputs/essence-10.jpg'></td><td><img src='../style/essence-10-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-10.png'></td><td></td></tr></table>


    ['I am a daughter, sister, friend, and advocate', "I advocate for those who don't have a voice", ' I care so deeply about children involved in the system and I will do almost anything to help them!']
    ['advocate', 'voice', 'system']



<table><tr><td><img src='../EssenceOutputs/essence-44.jpg'></td><td><img src='../style/essence-44-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-44.png'></td><td></td></tr></table>


    ['an inquisitive person', 'friendly and approachable', ' a desire to always learn new things']
    ['inquisitive', 'approachable', 'desire']



<table><tr><td><img src='../EssenceOutputs/essence-26.jpg'></td><td><img src='../style/essence-26-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-26.png'></td><td></td></tr></table>


    ['I am a working mom.', 'I am calm, determined, and loving.', ' The essence of what makes me is my compassion and caring.']
    ['mom', 'determined', 'compassion']



<table><tr><td><img src='../EssenceOutputs/essence-48.jpg'></td><td><img src='../style/essence-48-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-48.png'></td><td></td></tr></table>


    ["I'm a wife and mother of 5 children.", 'I am introverted, honest and generous.', ' My Catholic faith is a big part of who I am and how I live my life.']
    ['children', 'generous', 'catholic']



<table><tr><td><img src='../EssenceOutputs/essence-32.jpg'></td><td><img src='../style/essence-32-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-32.png'></td><td></td></tr></table>


    ['i am a hard working smart female', 'im funny yet clever and warm', ' love for animals and others makes me who i am']
    ['smart', 'clever', 'animals']



<table><tr><td><img src='../EssenceOutputs/essence-39.jpg'></td><td><img src='../style/essence-39-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-39.png'></td><td></td></tr></table>


    ['A girl', 'I am silly', 'I love dogs']
    ['girl', 'silly', 'dogs']



<table><tr><td><img src='../EssenceOutputs/essence-62.jpg'></td><td><img src='../style/essence-62-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-62.png'></td><td></td></tr></table>


    ['I AM A MIDDLE AGED PROFESSIONAL GRAPHICS DESIGNER.', 'I AM CHARMING AND CREATIVE.', 'I AM ARTISTIC AND CREATIVE. CAN I DESIGN SOMETHING FOR YOU? ANYTHING, YOU NAME IT.']
    ['graphics', 'charming', 'design']



<table><tr><td><img src='../EssenceOutputs/essence-73.jpg'></td><td><img src='../style/essence-73-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-73.png'></td><td></td></tr></table>


    ['I am a female.', 'I am outgoing, outspoken, and caring and funny.', 'My ability to approach things from a mindful perspective of others, even if not so much for myself.']
    ['female', 'outspoken', 'mindful']



<table><tr><td><img src='../EssenceOutputs/essence-80.jpg'></td><td><img src='../style/essence-80-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-80.png'></td><td></td></tr></table>


    ['I am a woman in my early 30s struggling to find success and fulfillment in life.', 'I am cynical, edgy and crafty.', 'My wry sense of humor']
    ['fulfillment', 'edgy', 'wry']



<table><tr><td><img src='../EssenceOutputs/essence-72.jpg'></td><td><img src='../style/essence-72-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-72.png'></td><td></td></tr></table>


    ['I am an artist.', 'I am quiet and energetic.', 'I am a woman of divine origins, living on Earth at this time.']
    ['artist', 'energetic', 'origins']



<table><tr><td><img src='../EssenceOutputs/essence-66.jpg'></td><td><img src='../style/essence-66-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-66.png'></td><td></td></tr></table>


    ['I am a twin.', 'I am very creative', 'What makes me who I am is my strive to achieve my goals.']
    ['twin', 'creative', 'strive']



<table><tr><td><img src='../EssenceOutputs/essence-67.jpg'></td><td><img src='../style/essence-67-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-67.png'></td><td></td></tr></table>


    ['I am a self confident woman who is loyal and generous.', 'I have an outgoing personality and love to travel!', 'I have a nurturing soul and find my peace in nature.']
    ['confident', 'travel', 'peace']



<table><tr><td><img src='../EssenceOutputs/essence-71.jpg'></td><td><img src='../style/essence-71-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-71.png'></td><td></td></tr></table>


    ['I am Leigh Ann Little -- publisher, writer, historian, lover of classic films, parent, and servent of Yahwey (in reverse order).', "I am extremely devoted to serving the Lord and making the world a better place through activism and publishing, and I'm a nostalgia buff as well, devoting lots of time to preserving historical things..", 'The essence of what makes me ME is quite simple -- I was put on this planet by a deity named Yahweh to fulfill HIS purposes, and enjoy the benfitis of living on this planet with His many blessings and protection.']
    ['classic', 'preserving', 'planet']



<table><tr><td><img src='../EssenceOutputs/essence-74.jpg'></td><td><img src='../style/essence-74-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-74.png'></td><td></td></tr></table>


    ['A man with a plan', 'Honest and loyal', 'Integrity']
    ['plan', 'loyal', 'integrity']



<table><tr><td><img src='../EssenceOutputs/essence-70.jpg'></td><td><img src='../style/essence-70-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-70.png'></td><td></td></tr></table>


    ['am a christian', 'i love the lord', 'love']
    ['christian', 'lord', 'love']



<table><tr><td><img src='../EssenceOutputs/essence-85.jpg'></td><td><img src='../style/essence-85-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-85.png'></td><td></td></tr></table>


    ['I am a young female wife.', 'I am intelligent, quiet, & an introvert.', 'My interests make me who I am: video games, books, exercise, food']
    ['young', 'introvert', 'exercise']



<table><tr><td><img src='../EssenceOutputs/essence-86.jpg'></td><td><img src='../style/essence-86-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-86.png'></td><td></td></tr></table>


    ['I am a traveling artist and dancer.', "I'm brave and smart and very much in love. I have vices but I try to balance them. I love the world and am generally excited about life.", "A deep spinning twirling gyroscopic, bright-eyed jewel full of love and joy. I realize that's kind of a weird thing to say but it's my real answer."]
    ['traveling', 'vices', 'twirling']



<table><tr><td><img src='../EssenceOutputs/essence-118.jpg'></td><td><img src='../style/essence-118-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-118.png'></td><td></td></tr></table>


    ['I am an intelligent thirty-something single female.', 'I am kind-hearted and soft-spoken, gentle, and helpful.', 'I am very quirky and have unique interests, but very wise.']
    ['single', 'gentle', 'wise']



<table><tr><td><img src='../EssenceOutputs/essence-130.jpg'></td><td><img src='../style/essence-130-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-130.png'></td><td></td></tr></table>


    ['I am a woman', 'I am loving, kind, caring, patient and guarded', 'I love books, cats, relaxing, travel and my family']
    ['woman', 'guarded', 'relaxing']



<table><tr><td><img src='../EssenceOutputs/essence-129.jpg'></td><td><img src='../style/essence-129-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-129.png'></td><td></td></tr></table>


    ['I am Catholic.', 'I try to be holy.', 'I am the creation of our Lord Jesus Christ.']
    ['catholic', 'holy', 'creation']



<table><tr><td><img src='../EssenceOutputs/essence-101.jpg'></td><td><img src='../style/essence-101-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-101.png'></td><td></td></tr></table>


    ['I am a beautiful queen.', 'I am like a warm summer day walking in the park with a breeze and you just got your favorite ice cream.', 'My faith in GOD.']
    ['queen', 'summer', 'faith']



<table><tr><td><img src='../EssenceOutputs/essence-114.jpg'></td><td><img src='../style/essence-114-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-114.png'></td><td></td></tr></table>


    ['I am a kind person', 'I am adventurous and friendly.', 'My love for travel and music']
    ['kind', 'adventurous', 'travel']



<table><tr><td><img src='../EssenceOutputs/essence-112.jpg'></td><td><img src='../style/essence-112-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-112.png'></td><td></td></tr></table>


    ['I am an older female who is married and a mother of three.', 'I am quiet until I get to know you. I am kind and considerate and I care about people.', 'My past experiences in life and with people all make up who I am.']
    ['older', 'considerate', 'past']



<table><tr><td><img src='../EssenceOutputs/essence-102.jpg'></td><td><img src='../style/essence-102-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-102.png'></td><td></td></tr></table>


    ['I am a mother.', "I'm very controlling.", 'I am very complex.']
    ['mother', 'controlling', 'complex']



<table><tr><td><img src='../EssenceOutputs/essence-104.jpg'></td><td><img src='../style/essence-104-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-104.png'></td><td></td></tr></table>


    ['I work at a library and am a mother of three.', 'I am friendly and helpful.', 'I am generous and caring.']
    ['library', 'helpful', 'generous']



<table><tr><td><img src='../EssenceOutputs/essence-131.jpg'></td><td><img src='../style/essence-131-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-131.png'></td><td></td></tr></table>


    ['I am a skeptic', 'I question everything', 'I take nothing for granted. I make others think about things in a different way. I am the opposite of ordinary.']
    ['skeptic', 'question', 'granted']



<table><tr><td><img src='../EssenceOutputs/essence-144.jpg'></td><td><img src='../style/essence-144-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-144.png'></td><td></td></tr></table>


    ['I am a respected, kind, professional person.', "I'm a very reasonable, fun, and energetic.", 'My great personality, being compassionate, and having empathy makes me who I am.']
    ['respected', 'reasonable', 'empathy']



<table><tr><td><img src='../EssenceOutputs/essence-132.jpg'></td><td><img src='../style/essence-132-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-132.png'></td><td></td></tr></table>


    ['I am a wife and a mother.', 'I am kind and caring and hard working.', 'I am a family person who loves to cacre for others.']
    ['wife', 'working', 'care']



<table><tr><td><img src='../EssenceOutputs/essence-138.jpg'></td><td><img src='../style/essence-138-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-138.png'></td><td></td></tr></table>


    ['A loving, compassionate, loyal woman to friends and family.', "I'm laid back, fun, easy going and forgiving", 'Jesus is the essence of all that is good in me.']
    ['loyal', 'forgiving', 'jesus']



<table><tr><td><img src='../EssenceOutputs/essence-137.jpg'></td><td><img src='../style/essence-137-style.png' width='400' height='400'></td><td><img src='../EssenceStyles/styled-essence-137.png'></td><td></td></tr></table>
