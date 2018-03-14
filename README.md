
# Dictionaries 

### Introduction

We've spent the last couple of sections talking about one type of collection in Python, a list.  And as we know we use lists to represent a collection of information that is ordered, like a list of the most watched TV shows.  Now, othertimes we group data together to represent attributes of the same entity.  For example, various attributes of a single TV show.  For that, we can use a dictionary.

### Learning Objectives

### Creating a dictionary, and retrieving attributes

Imagine we want to represent information about the TV show friends in Python.  Our first step, might be to go to Wikipedia to find some information.

![](./friends.png)

As you can see this information is presented in two columns, with the topics or headings to the left, and their specific values to the right.  Here is some of the above information represented as a dictionary in Python.


```python
friends = {'name': 'Friends', 'genre': 'sitcom', 'no_of_seasons': 10}
```

We create a dictionary with the braces, also called curly braces, located above the return key.  (We need to press shift to get them).  A dictionary is a collection of key, value pairs.  With each pair having one key to the left and the corresponding value to the right.      

Now that we have initialized a dictionary and assigned it to the variable, `friends`, we can retrieve the hash, as well as the associated values.


```python
friends
```




    {'genre': 'sitcom', 'name': 'Friends', 'no_of_seasons': 10}




```python
friends['no_of_seasons']
```




    10



So to retrieve a specific value, we simply reference the dictionary, followed by the brackets, followed by the key.  We receive the corresponding value in return. 

### Assigning attributes and exploring the edge cases

Now that we know how to retrieve values, let's take our existing `friends` dictionary, and assign it more key value pairs.  Here is what our dictionary currently looks like.


```python
friends
```




    {'genre': 'sitcom', 'name': 'Friends', 'no_of_seasons': 10}



Let's add a key of `no_of_episodes` with a value of 236.


```python
friends['no_of_episodes'] = 236
```


```python
friends
```




    {'genre': 'sitcom',
     'name': 'Friends',
     'no_of_episodes': 236,
     'no_of_seasons': 10}



So you can see that our values of a dictionary do not just have to be strings, but can be other datatypes like numbers.  What about the keys, can they be other datatypes like numbers?  With programming, we don't have to look up the answer.  We can just try things.


```python
friends[14] = 'some value'
```


```python
friends[14]
```




    'some value'



Apparently so.

Ok, let's get rid of that key - it doesn't make much sense.


```python
del friends[14]
```

We use the delete function followed by the dictionary and the name of the key.  And now it's gone.


```python
friends
```




    {'genre': 'sitcom',
     'name': 'Friends',
     'no_of_episodes': 236,
     'no_of_seasons': 10}



### Dictionaries with arrays

If you look back up at our Friends table, you will see that there are two creators.  It probably makes sense to think of these creators as a list.


```python
creators = ['David Crane', 'Marta Kauffman']
```

So let's have our `friends` dictionary have a key of creators that points to this list. 


```python
friends['creators'] = ['David Crane', 'Marta Kauffman']
```


```python
friends
```




    {'creators': ['David Crane', 'Marta Kauffman'],
     'genre': 'sitcom',
     'name': 'Friends',
     'no_of_episodes': 236,
     'no_of_seasons': 10}




```python
friends['creators']
```




    ['David Crane', 'Marta Kauffman']



And of course, if we want to get the first creator in the list, and store it as a variable, we can.


```python
friends['creators'][0]
```




    'David Crane'



We reference the dictionary, then get to the list of creators through using the key creators.  And now that we are pointing to that list we use the brackets to reference the string at index zero.

###  Lists of Dictionaries

Now imagine we want to represent another TV show.

![](./seinfeld.png)

As you can see, similar data is provided and represented as we had for Friends.


```python
friends
```




    {'creators': ['David Crane', 'Marta Kauffman'],
     'genre': 'sitcom',
     'name': 'Friends',
     'no_of_episodes': 236,
     'no_of_seasons': 10}



  Ok let's get that same information for Seinfeld.


```python
seinfeld = {'name': 'Seinfeld', 'creators': ['Larry David', 'Jerry Seinfeld'], 'genre': 'sitcom', 'no_of_seasons': 10, 'no_of_episodes': 180}
```


```python
seinfeld
```




    {'creators': ['Larry David', 'Jerry Seinfeld'],
     'genre': 'sitcom',
     'name': 'Seinfeld',
     'no_of_seasons': 10}



Now that you we have two TV shows, you may think that we have a list of TV shows.


```python
tv_shows = [friends, seinfeld]
tv_shows
```




    [{'creators': ['David Crane', 'Marta Kauffman'],
      'genre': 'sitcom',
      'name': 'Friends',
      'no_of_episodes': 236,
      'no_of_seasons': 10},
     {'creators': ['Larry David', 'Jerry Seinfeld'],
      'genre': 'sitcom',
      'name': 'Seinfeld',
      'no_of_episodes': 180,
      'no_of_seasons': 10}]



This is a nested data structure.  And it can be confusing to disentangle.  A good technique is to describe the data structure first before working with it.

So `tv_shows` is a list a list, with each element of the list a dictionary.  The dictionary has a key of `creators` which itself points to another list.  So in describing the data structure, just look to the braces and brackets at the very beginning.  `[{` means we are starting an list with a dictionary as the first element.  

Ok, let's start working with this nested data structure.  First let's select the second creator of Seinfeld and set it equal to the variable `jerry`.


```python
tv_shows[1]
```




    {'creators': ['Larry David', 'Jerry Seinfeld'],
     'genre': 'sitcom',
     'name': 'Seinfeld',
     'no_of_episodes': 180,
     'no_of_seasons': 10}



Now we have the correct TV show.  Let's keep going.


```python
tv_shows[1]['creators']
```




    ['Larry David', 'Jerry Seinfeld']



Ok, almost there, we have our list of creators.


```python
tv_shows[1]['creators'][1]
```




    'Jerry Seinfeld'



Now we see we are selecting the correct creator from the list.


```python
jerry = tv_shows[1]['creators'][1]
jerry
```




    'Jerry Seinfeld'



So as you can see, we broke this problem down into steps.  We first selected the correct TV show.  Then, we moved onto the `creators` attribute.  Finally, we retrieved the correct element from the list of creators.  

As programmers, we tend not to get much smarter over time.  But we develop skills for making problems easier to solve.  Taking the problem in steps, and checking our work at each of these steps is a technique we should continue to lean on.

### Summary

In this section, we saw a new type of collection, the dictionary.  A dictionary is a sequence of key value pairs.  We mark the start and end of a dictionary with curly braces, `{}`, and then follow the pattern of `'key':'value'` for each of the associated attributes, with each attribute separated by a comma: `dictionary = {'key1':'value1', 'key2':'value2'}`.  

We retrieve a specific value from a dictionary by using the bracket accessor in combination with the key, so `dictionary['key2]'` returns `'value2'`.  And we add a new attribute with the format `dictionary['key3'] = 'value3'`.

Finally, we saw that we can represent data as nested data structures.  In working with nested data structures a good technique is to pay attention to the edges of the data structure as in `[{`, and then articulate how that data structure is nested.  Finally, when accessing data from a nested data structure it is useful to break down the problem into steps to get feedback along the way.
