# Algorithms - Basic Sorts
***
***
# Bubble Sort - Intro
* sort a list
* to sort a list:
    * you compare the first item to the second item
    * if the first item is smaller then you switch them around
    * then you compart the second item to the third...
    * etc... all the way down the list
    * what happens is you keep running these comparisons on the list until its fully sorted

***
***
# Bubble Sort
* range(len(list) - 1, 0 , -1):
    * len - 1 ...self explanitory
    * 0 go down to 0
    * - 1 decriment by 1 (starting at the tail end)
* the second for loop moves forward through the list
    * for j in range(i)
```
def bubble_sort(my_list):
    for i in range(len(my_list) - 1, 0 ,-1):
        for j in range(i):
            if my_list[j] > my_list[j+1]:
                temp = my_list[j]
                my_list[j] = my_list[j+1]
                my_list[j+1] = temp
    return my_list


print(bubble_sort([4,2,6,5,1,3]))
```

***
***
# Selection Sort - Intro
* you keep track of the index for the minimum value 
  * the index not the value
```
def selection_sort(my_list):
    for i in range(len(my_list)-1):
        min_index = i
        for j in range(i+1, len(my_list)):
            if my_list[j] < my_list[min_index]:
                min_index = j
        if i != min_index:
            temp = my_list[i]
            my_list[i] = my_list[min_index]
            my_list[min_index] = temp
    return my_list


print(selection_sort([4,2,6,5,1,3]))
```

***
***
# Insertion Sort - Intro
* you start with the second item in the list, you then compare it with the item before it
* if its less than the item before you swap them
* then you move to the next items and compare it to the items before it 


***
***
# Insertion Sort - Code

```
def insertion_sort(my_list):
    for i in range(1, len(my_list)):
        temp = my_list[i]
        j = i-1
        while temp < my_list[j] and j > -1:
            my_list[j+1] = my_list[j] 
            my_list[j] = temp
            j -= 1
    return my_list


print(insertion_sort([4,2,6,5,1,3]))
```