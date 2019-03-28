# NPL_Sentiment_Analysis (Pickle & Module)
> Natural Language Processing --- Movie review Sentiment Analysis
> Learn how to convert python object into a byte stream (more efficient programming)

---
>#### Why pickling
>With training models, we often need to store the trained model so that the model can be read directly when making decisions without retraining the model, which saves time.

---
## Installation

```python
pip install pickle
```

## The Basics

The pickle module in Python is used to store document information in the program and store it locally in **binary** form and can be read out.
There are two basic methods:

```python
pickle.dump(obj,file)    #save
pickle.load(file)        #read
```
Here is a quick example of how to save and load .pickle file.

```python

import pickle
dataList = [[1, 5, 'yes'],
            [2, 4, 'yes'],
            [3, 3, 'no'],
            [4, 2, 'no'],
            [5, 1, 'no']]
dataDic = { 0: [1, 2, 3, 4, 5],
            1: ('yes', 'no'),
            2: {'1':'yes','2':'yes','3':'yes','4':'no','5':'no'}}
 
# Using dump to save the object by serialization
fw = open('dataFile.txt','wb')
# Pickle the list using the highest protocol available.
pickle.dump(dataList, fw, -1)
# Pickle dictionary using protocol 0.
pickle.dump(dataDic, fw)
fw.close()
 
# Using load to read the serialized .pickle file
fr = open('dataFile.txt','rb')
data1 = pickle.load(fr)
print(data1)
data2 = pickle.load(fr)
print(data2)
fr.close()
```
The results is shown below:
```python
[[1, 5, 'yes'], [2, 4, 'yes'], [3, 3, 'no'], [4, 2, 'no'], [5, 1, 'no']]
{0: [1, 2, 3, 4, 5], 1: ('yes', 'no'), 2: {'1': 'yes', '2': 'yes', '3': 'yes', '4': 'no', '5': 'no'}}
```
## A Example of comment snetiment analysis

- First we trained the model based on the [positive.text](https://github.com/parrently/NPL_Sentiment_Analysis-Pickle_-_Module-/blob/master/positive.txt) and [negative.text](https://github.com/parrently/NPL_Sentiment_Analysis-Pickle_-_Module-/blob/master/negative.txt) data, then saved them to pickle files --- [NLP_Creating a module for Sentiment Analysis.py](https://github.com/parrently/NPL_Sentiment_Analysis-Pickle_-_Module-/blob/master/NLP_Creating%20a%20module%20for%20Sentiment%20Analysis.py)

- Second we reload the pickle and rerun the module (It is faster we you try to import the model again) --- [sentiment_mode.py] (https://github.com/parrently/NPL_Sentiment_Analysis-Pickle_-_Module-/blob/master/sentiment_mod.py)

- Type any comment to test the sentiment analysis [test_senetiment_mod.py](https://github.com/parrently/NPL_Sentiment_Analysis-Pickle_-_Module-/blob/master/test_sentiment_mod.py)

```python
import sentiment_mod as s
print(s.sentiment("This movie was awesome! The acting was great, plot was wonderful, and there were pythons...so yea!"))
print(s.sentiment("This movie was utter junk. There were absolutely 0 pythons. I don't see what the point was at all. Horrible movie, 0/10"))
```
```markdown
('pos', 1.0)
('neg', 1.0)
We can see that the first comment we created is showing 100% confident as a positive review, and the second one is 100% negative.
```

@Copyright The NLP_saving_classifiers.py file was re-written based on [Sentdex](https://pythonprogramming.net/pickle-classifier-save-nltk-tutorial/) turorials from python programming.
