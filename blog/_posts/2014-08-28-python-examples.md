---
id: 589
title: Python examples
date: 2014-08-28T19:36:02-05:00
author: Alan Verdugo
layout: post
guid: http://www.kippel.net/blog/?p=589
permalink: /blog/python-examples
#permalink: /?p=589
categories:
  - Uncategorized
tags:
  - english
  - IT
  - Technical writing
---
<p style="text-align: justify;">
      I had a lot of fun doing Python exercises for an online training course I took. Here are several of them that could be useful if somebody else is learning Python (or programming). Double click on the code to get the code in plain text.
</p>

<pre class="theme:terminal font:ubuntu-mono font-size-enable:false toolbar:2 striped:false wrap:true lang:python decode:true" title="Disemvoweler">#!/usr/bin/env python
'''
    This program asks the user for text, removes any vowels on it and prints the "unvoweled" text to the user.
    ("y"/"Y" is not considered a vowel because that is just silly).
'''
vowels=["a","e","i","o","u","A","E","I","O","U",]
text = raw_input("Enter text, I will remove the vowels: ")
text_list=[]
position=0
for char in str(text):
    text_list.append(char)
    if char in vowels:
        text_list[position]=""
    position=position+1
print "".join(text_list)</pre>

<pre class="theme:terminal font:ubuntu-mono font-size-enable:false toolbar:2 show-lang:1 striped:false wrap:true lang:python decode:true" title="Censorer">#!/usr/bin/env python
'''
    This program will censor a given word in a given text. E.g. if the user types "This is my text!" and the word "text" is to be censored, the program will return "This is my ****!"
    This program is easy, but you need to make sure to censor the whole word in the text, and not just censor the characters that appear in the word.
    This is because there probably will be occurrences of those characters in other words that should not be censored. So you need to find the whole word before doing any censoring.
'''
text = raw_input("Enter the text to censor: ")
word = raw_input("Enter the word to censor: ")
asterisks=""
attemp_word=[]
word_list="".join(word)
counter=0
for char in str(text):
    for char2 in word:
        if char == word_list[counter]:
            attemp_word.append(char)
            asterisks=asterisks+"*"
            counter=counter+1
            if "".join(attemp_word)==word and counter == len(word):
                print text.replace(word,asterisks)
                asterisks=""
                attemp_word=[]
                counter=0</pre>

<pre class="theme:terminal font:ubuntu-mono font-size-enable:false toolbar:2 show-lang:1 striped:false wrap:true lang:python decode:true" title="List comprehension">#!/usr/bin/env python
# This program uses list comprehension to print the cubes of the numbers 1 to 10 that are evenly divisible by 4.
cubes_by_four=[x*x*x for x in range(1,11) if ((x*x*x)%4 == 0)]
print cubes_by_four</pre>

<pre class="theme:terminal font:ubuntu-mono font-size-enable:false toolbar:2 show-lang:2 striped:false wrap:true lang:python decode:true" title="Squares">#!/usr/bin/env python
# This program uses list comprehension to print the squares of the numbers 1 to 10 that are even.
even_squares=[x*x for x in range(1,12) if (x%2 == 0)]
print even_squares</pre>

<pre class="theme:terminal font:ubuntu-mono font-size-enable:false toolbar:2 show-lang:2 striped:false wrap:true lang:python decode:true" title="Slicing">#!/usr/bin/env python
'''
    Use list slicing to print out every odd index element of my_list (numbers from 1 to 10) from start to finish.
Omit the start and end index. You only need to specify a stride.

    Remember, the syntax for list slicing is [start:end:stride]

    Since you're using the entire list, you should leave out the start and end indices (but leave in the colons!)
and give the slice a stride that will select every other (that is, odd) element.
'''
my_list=range(1,11) # List of number from 1 to 10.
print my_list[::2]</pre>

<pre class="theme:terminal font:ubuntu-mono font-size-enable:false toolbar:2 show-lang:2 striped:false wrap:true lang:python decode:true">#!/usr/bin/env python
'''
    This one takes a list of integers as input and returns the product of all of the elements in the list.

    For example: product([4, 5, 5]) should return 100 (because 4 * 5 * 5 is 100).

    For now, we will not worry about the list being empty.
'''
my_numbers = raw_input("Enter the list of numbers: ")
# We start with the result at 1 in order to avoid a multiplication by 0.
result=1
for my_number in my_numbers:
    result = result*int(my_number)
print "The product of your numbers is:",result</pre>

<pre class="theme:terminal font:ubuntu-mono font-size-enable:false toolbar:2 striped:false wrap:true lang:python decode:true" title="Odd removers">#!/usr/bin/env python
'''
    This one takes in a list named my_numbers, removes all odd numbers in the list, and returns the result.
    For example, [1,2,3] should return [2].
    This will not directly modify the list it is given as input; instead, it will return a new list with only the even numbers.
'''
my_numbers = raw_input("Enter the list of numbers: ")
new_list=[]
for my_number in my_numbers:
    if int(my_number)%2 == 0:
        new_list.append(my_number)
print new_list</pre>

<pre class="theme:terminal font:ubuntu-mono font-size-enable:false toolbar:2 striped:false wrap:true lang:python decode:true" title="Iterator">#!/usr/bin/env python
# These are just a couple of examples of for loops.
# Place values into a list named "items"
items = ["Alpha", "Beta", "Gamma", "Delta", "Epsilon", "Omega"]

# Lets do this in functions since were are so fancy...
def printItems(items):
    # Iterates over list, running statements for each item in the list
    count=0
    for item in items:
        count+=1
        # Note: commas in print statements separate the items by a single space
        print "This is item #%s:" % count,item

def printWithFormatting(items):
    # Iterates over list, running statements for each item in the list
    print "Now lets do it with string formatting!"
    count=0
    for item in items:
        count+=1
        # Note: commas in print statements separate the items by a single space
        print "This is item #{0}:".format(count),format(item)

# Functions are called
printItems(items)
printWithFormatting(items)</pre>

<pre class="theme:terminal font:ubuntu-mono font-size-enable:false toolbar:2 striped:false wrap:true lang:python decode:true" title="Subprocess">#!/usr/bin/env python
# This is just an example of calling OS functions from Python.
import subprocess
subprocess.call("ls -l", shell=True)</pre>

<pre class="theme:terminal font:ubuntu-mono font-size-enable:false toolbar:2 striped:false wrap:true lang:python decode:true">#!/usr/bin/env python
'''
    This one takes in a list and removes elements of the list that are the same.
    For example, if the user inputs ([1,1,2,2]), the program should return [1,2].
    We will not remove every occurrence, since you need to keep a single occurrence of a number.
    The order in which you present your output does not matter. So returning [1,2,3] is the same as returning [3,1,2].
    Do not modify the list you take as input! Instead, return a new list.
'''
text = raw_input("Enter the text to remove duplicates from: ")

'''
    We convert to a set and back into a list. Sets are collections of unique items. So converting our list into a set will automatically remove duplicates. The drawback is that, since the sets are unordered, the order will be lost.
'''
my_set = set(text)
result = list(my_set)
print result</pre>

<pre class="theme:terminal font:ubuntu-mono font-size-enable:false toolbar:2 striped:false wrap:true lang:python decode:true" title="Reverser">#!/usr/bin/env python
# This program reverses strings. (E.g. "radar" will return "radar")
list1=[]
current_position=0
text = raw_input("Enter your string to be reversed: ")
for n in str(text):
    list1.append("")
current_position = len(text)
for c in text:
    list1[current_position-1]=c
    current_position=current_position-1
print "Your reversed string:","".join(list1)</pre>

<pre class="theme:terminal font:ubuntu-mono font-size-enable:false toolbar:2 striped:false wrap:true lang:python decode:true " title="Scrabble">#!/usr/bin/env python
# This program uses a dictionary to score Scrabble words. (I have never played scrabble, so I am not sure if these are the correct rules but I reckon this is the basic algorithm)
score= {"a":1,"b":3,"c":3,"d":2,"e":1,"f":4,"g":2,"h":4,"i":1,"j":8,"k":5,"l":1,"m":3,
"n":1,"o":1,"p":3,"q":10,"r":1,"s":1,"t":1,"u":1,"v":4,"x":8,"y":4,"z":10}

word = raw_input("Enter text, I will score it: ")
word=word.lower()
sum=0

for char in str(word):
    if char in score:
        sum=sum+score[char]
print "Your score:",sum</pre>