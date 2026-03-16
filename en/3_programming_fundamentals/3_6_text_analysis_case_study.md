# Text Analysis (Case Study)

## What is text analysis?

Text analysis, also known as text mining or text analytics, refers to the process of extracting meaningful information and insights from textual data.

## Objectives

- Use Python commands to perform text analysis.
- Convert the text to lowercase and then find and count the frequency of all unique words, as well as a specified word.

## Setup

**Let's consider a real-life scenario where you are analyzing customer feedback for a product. You have a large data set of customer reviews in the form of strings, and you want to extract useful information from them using the three identified tasks:**

**Task 1. String in lowercase:** You want to pre-process the customer feedback by converting all the text to lowercase. This step helps standardize the text. Lower casing the text allows you to focus on the content rather than the specific letter casing.

**Task 2. Frequency of all words in a given string:** After converting the text to lowercase, you want to determine the frequency of each word in the customer feedback. This information will help you identify which words are used more frequently, indicating the key aspects or topics that customers are mentioning in their reviews. By analyzing the word frequencies, you can gain insights into the most common issues raised by customers.

**Task 3. Frequency of a specific word:** In addition to analyzing the overall word frequencies, you want to specifically track the frequency of a particular word that is relevant to your analysis. For example, you might be interested in monitoring how often the word "reliable" appears in customer reviews to gauge customer sentiment about the product's reliability. By focusing on the frequency of a specific word, you can gain a deeper understanding of customer opinions or preferences related to that particular aspect.

By performing these tasks on the customer feedback dataset, you can gain valuable insights into customer sentiment

## Steps

### 1. Define a string

```python
givenstring="Lorem ipsum dolor! diam amet, consetetur Lorem magna. sed diam nonumy eirmod tempor. diam et labore? et diam magna. et diam amet."
```

### 2.  **Define the class and its attributes**

```python
# Let's create a class called TextAnalyzer to analyze text.
class TextAnalyzer(object):
    # The __init__ method initializes the class with a 'text' parameter.
    # You will store the provided 'text' as an instance variable.
    def __init__(self, text):
```

### 3. **Implement a code to format the text**

```python
class TextAnalzer(object):
    
    def __init__ (self, text):
        # remove punctuation
        formattedText = text.replace('.','').replace('!','').replace('?','').replace(',','')
        
        # make text lowercase
        formattedText = formattedText.lower()
        
        self.fmtText = formattedText
```

### **4. Implement a code to count the frequency of all unique words**

```python
class TextAnalyzer(object):
    
    def __init__ (self, text):
        # remove punctuation
        formattedText = text.replace('.','').replace('!','').replace('?','').replace(',','')
        
        # make text lowercase
        formattedText = formattedText.lower()
        
        self.fmtText = formattedText
        
    def freqAll(self):        
        # split text into words
        wordList = self.fmtText.split(' ')
        
        # Create dictionary
        freqMap = {}
        for word in set(wordList): # use set to remove duplicates in list
            freqMap[word] = wordList.count(word)
        
        return freqMap
```

### 5. Implement a code to count the frequency of a specific word

```python
class TextAnalyzer(object):
    
    def __init__ (self, text):
        # remove punctuation
        formattedText = text.replace('.','').replace('!','').replace('?','').replace(',','')
        
        # make text lowercase
        formattedText = formattedText.lower()
        
        self.fmtText = formattedText
        
    def freqAll(self):        
        # split text into words
        wordList = self.fmtText.split(' ')
        
        # Create dictionary
        freqMap = {}
        for word in set(wordList): # use set to remove duplicates in list
            freqMap[word] = wordList.count(word)
        
        return freqMap
    
    def freqOf(self,word):
        # get frequency map
        freqDict = self.freqAll()
        
        if word in freqDict:
            return freqDict[word]
        else:
            return 0
```