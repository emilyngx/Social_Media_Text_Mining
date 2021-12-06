## Import Regex
```python
import re
```
## Create a list
```python
X = ["This is a # scary wolf! ",
    "welcome to a mysterious  jungle",
    "2020 was the year to remember forever_never",
    "Remember the name s - John",
    "I      admire      you"]
print(X)
```
![alt text](https://github.com/emilyngx/SocialMedia_TextMining/blob/main/Cleaning%20using%20Regex/images/1.png)
## Iterate through the list & Clean it
``` python
i = 0
while i < len(X):
    X[i] = re.sub(r"\W"," ",X[i]) #remove ASCII symbols
    X[i] = re.sub(r"_.*$","",X[i]) #remove any zero or more character
    X[i] = re.sub(r"[#!_-]","",X[i]) #remove special characters
    X[i] = re.sub(r"\d","",X[i]) #remove digits
    X[i] = re.sub(r"\s+"," ",X[i]) #replace one or more space with one
    X[i] = re.sub(r"\s+[a-zA-Z]\s+"," ",X[i]) #remove whitespaces 
    X[i] = re.sub(r"^[ \t]+|[ \t]+$","",X[i]) #remove a space at the begininning and the end of a sentence
    X[i] = X[i].lower()
    X[i] = re.sub(r"i\s+","I ", X[i]) #Make i a capital letter
    i += 1
for i in X:
    print(i)
```
![alt text](https://github.com/emilyngx/SocialMedia_TextMining/blob/main/Cleaning%20using%20Regex/images/0.png)
