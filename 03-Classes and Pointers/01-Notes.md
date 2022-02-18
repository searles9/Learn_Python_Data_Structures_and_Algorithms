# Classes and Pointers
***
***
# Classes
* a class is like a cookie cutter
* when you make a class you make a datatype (for example an integer is a data type)
* the class name is cookie 
* the def__init__ part is called a constructor 
```
class Cookie:
    def __init__(self, color):
        self.color = color 

    def get_color(self):
        return self.color

    def set_color(self, color):
        self.color = color

cookie_one = Cookie("green")
cookie_two = Cookie("blue")

cookie_one.set_color("yellow")
print("Cookie one is", cookie_one.get_color())
```
* example with linked list:
```
class LinkedList:
    def __init__(self, value):
        ...

    def append(self,value):
        ...

    def pop(self):
        ...

    def prepend(self, value):
        ...

    def insert(self, index, value):
        ...

    def remove(self, index):
        ...
```

***
***
# Pointers
* this creates a new number its not a direct link or refrence to the original
```
num1 = 11
num2 = num1
```
* this better shows that
```
num1 = 11
num2 = num1

num 1 = 22

print(num2) 

# this prints 11 because it is not a pointer
```
* with dictionaries this is different though
* dict2 makes a direct pointer to dict 1
* if dict1 changes so does dict2
```
dict1 = {
    "value": 11
}

dict2 = dict 1
```