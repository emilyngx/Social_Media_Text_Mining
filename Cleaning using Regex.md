```python
import re
```


```python
#Import a list and use Regex to iterate in the list
X = ["This is a # scary wolf! ",
    "welcome to a mysterious  jungle",
    "2020 was the year to remember forever_never",
    "Remember the name s - John",
    "I      admire      you"]
print(X)
```

    ['This is a # scary wolf! ', 'welcome to a mysterious  jungle', '2020 was the year to remember forever_never', 'Remember the name s - John', 'I      admire      you']



```python
# Iterate through the list and clean it
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
Y = X
print("Y")
print(*Y, sep = "\n")
```

    Y
    this is scary wolf
    welcome to mysterious jungle
    was the year to remember forever
    remember the name john
    I admire you



```python

```
