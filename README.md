# NPL_Sentiment_Analysis-Pickle_-_Module-
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



## A Example of comment snetiment analysis on classfication module based on Piclked classifiers

The NLP_saving_classifiers.py file was re-written based on [Sentdex](https://pythonprogramming.net/pickle-classifier-save-nltk-tutorial/) turorials from python programming.
