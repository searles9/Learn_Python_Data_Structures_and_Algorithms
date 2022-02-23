# Hash Tables
***
***
# Hash Table Intro
* you have an item, you run it through a hash and it gives you the address in the table
* hashes are one way, you cant take the table address and then get the original value back by running it through the hash again
* hash tables are deterministic 

***
***
# Hash Tables - Collisions 
* a collision happens when you put a ley value pair in a place where there was already a key value pair
* seperate chaining - you put multible values in the same spot in the table (you can use lists or linked lists)
* linear probing (open addressing) - if the space is occupied you go down until you find an empty address

***
***
# Hash Table - Constructor
* you should always have a prime number of addresses (even number)
    * even number means less collisions
* the __init__ function creates the data set
* the __hash function is what creates the hash
```
class HashTable:
    def __init__(self, size = 7):
        self.data_map = [None] * size
      
    def __hash(self, key):
        my_hash = 0
        for letter in key:
            my_hash = (my_hash + ord(letter) * 23) % len(self.data_map)
        return my_hash  

    def print_table(self):
        for i, val in enumerate(self.data_map): 
            print(i, ": ", val)

        
my_hash_table = HashTable()

my_hash_table.print_table()
```

***
***
# Hash Table - Set

```
class HashTable:
    def __init__(self, size = 7):
        self.data_map = [None] * size

    def print_table(self):
        for i, val in enumerate(self.data_map): 
            print(i, ": ", val)
      
    def __hash(self, key):
        my_hash = 0
        for letter in key:
            my_hash = (my_hash + ord(letter) * 23) % len(self.data_map)
        return my_hash  
    
    def set_item(self, key, value):
        index = self.__hash(key)
        if self.data_map[index] == None:
            self.data_map[index] = []
        self.data_map[index].append([key, value])
    
        
my_hash_table = HashTable()

my_hash_table.set_item('bolts', 1400)
my_hash_table.set_item('washers', 50)
my_hash_table.set_item('lumber', 70)

my_hash_table.print_table()
```

***
***
# Hash Table - Get

```
class HashTable:
    def __init__(self, size = 7):
        self.data_map = [None] * size
      
    def __hash(self, key):
        my_hash = 0
        for letter in key:
            my_hash = (my_hash + ord(letter) * 23) % len(self.data_map)
        return my_hash  

    def print_table(self):
        for i, val in enumerate(self.data_map): 
            print(i, ": ", val)
    
    def set_item(self, key, value):
        index = self.__hash(key)
        if self.data_map[index] == None:
            self.data_map[index] = []
        self.data_map[index].append([key, value])
    
    def get_item(self, key):
        index = self.__hash(key)
        if self.data_map[index] is not None:
            for i in range(len(self.data_map[index])):
                if self.data_map[index][i][0] == key:
                    return self.data_map[index][i][1]
        return None
             

my_hash_table = HashTable()

my_hash_table.set_item('bolts', 1400)
my_hash_table.set_item('washers', 50)

print(my_hash_table.get_item('bolts'))
print(my_hash_table.get_item('washers'))
print(my_hash_table.get_item('lumber'))
```

***
***
# Hash Table - Keys

```
class HashTable:
    def __init__(self, size = 7):
        self.data_map = [None] * size
      
    def __hash(self, key):
        my_hash = 0
        for letter in key:
            my_hash = (my_hash + ord(letter) * 23) % len(self.data_map)
        return my_hash  

    def print_table(self):
        for i, val in enumerate(self.data_map): 
            print(i, ": ", val)
    
    def set_item(self, key, value):
        index = self.__hash(key)
        if self.data_map[index] == None:
            self.data_map[index] = []
        self.data_map[index].append([key, value])
    
    def get_item(self, key):
        index = self.__hash(key)
        if self.data_map[index] is not None:
            for i in range(len(self.data_map[index])):
                if self.data_map[index][i][0] == key:
                    return self.data_map[index][i][1]
        return None

    def keys(self):
        all_keys = []
        for i in range(len(self.data_map)):
            if self.data_map[i] is not None:
                for j in range(len(self.data_map[i])):
                    all_keys.append(self.data_map[i][j][0])
        return all_keys
        

my_hash_table = HashTable()

my_hash_table.set_item('bolts', 1400)
my_hash_table.set_item('washers', 50)
my_hash_table.set_item('lumber', 70)

print(my_hash_table.keys())
```
***
***
# Hash Table - Big O
* the hash method itself is O(1)
* set item is - your just appending -O(1)
* get_items - O(n)

***
***
# Hash Table - Interview Questions
### Option 1 - determine if 2 lists have an item in common 
* the naive approach is to use a nested for loop - but that is O(n^2)
```
def item_in_common(list1, list2):
    for i in list1:
        for j in list2:
            if i == j:
                return True
    return False

list1 = [1,3,5]
list2 = [2,4,6]

print(item_in_common(list1, list2))
```
### Option 2 - determine if 2 lists have an item in common 
* loop through the first list - O(n)
* when you look through the second list its - O(n) again
* O(2n) is still O(n) which is more efficent than O(n^@)
```
def item_in_common(list1, list2):
    my_dict = {}
    for i in list1:
        my_dict[i] = True

    for j in list2:
        if j in my_dict:
            return True

    return False


list1 = [1,3,5]
list2 = [2,4,6]


print(item_in_common(list1, list2))
```

***
***
# Hash Table - Review
* Both Insert and Lookup by key in a Hash Table is O(1):
    * True
* Since a Hash Table is O(1) for Insert and Lookup it is always better than a Binary Search Tree:
    * Binary Search Trees are sorted which makes them better at searching for all values that fall within a range.
* Looking up a value in a Hash Table is O(1):
    * False - Key lookup is O(1) but not value.