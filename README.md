import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize

nltk.download('stopwords')
nltk.download('punkt')
example= "This is a sample sentence, showing off stop words."
stop_words= set(stopwords.words('english'))
word_tokens=word_tokenize(example,'english')
filtered_sentence=[w for w in word_tokens if not w.lower() in stop_words]
filtered_sentence = []
for w in word_tokens:
    if w not in stop_words:
        filtered_sentence.append(w)
print(word_tokens)
print(filt
print(filtered_sentence)


import numpy as np
 
def levenshtein(s1,s2):
    size_x=len(s1)+1
    size_y=len(s2)+1
    matrix=np.zeros((size_x, size_y))
    for x in range(size_x):
        matrix[x,0]=x

    for y in range(size_y):
        matrix[0,y]=y
    for x in range(1,size_x):
        for y in range(1,size_y):
            if s1[x-1] == s2[y-1]:
                matrix[x,y]=min(matrix[x-1,y]+ 1,matrix[x-1,y-1],matrix[x,y-1]+1)
            else:
                matrix[x,y]=min(matrix[x-1,y]+ 1,matrix[x-1,y-1]+1,matrix[x,y-1]+1)
    print(matrix)
    return(matrix[size_x-1,size_y-1])
levenshtein("Hallo","Hello")

import requests
from bs4 import BeautifulSoup

req = BeautifulSoup(requests.get("https://www.bing.com").text)
for link in req.find_all("a"):
    print(link.get("href"))
