---
id: 590
title: Python exercises
date: 2014-08-28T11:42:40-05:00
author: Alan Verdugo
layout: revision
guid: http://www.kippel.net/blog/?p=590
permalink: /?p=590
---
python examples

I had fun doing several Python exercises for an online training course I took. Here are several of them that could be useful if somebody else is learning Python (or programming).

#!/usr/bin/env python  
&#8221;&#8217;  
This program asks the user for text, remove any vowels on it and print the &#8220;unvoweled&#8221; text to the user.  
&#8220;y&#8221; is not considered a vowel because that is just silly.  
&#8221;&#8217;  
vowels=[&#8220;a&#8221;,&#8221;e&#8221;,&#8221;i&#8221;,&#8221;o&#8221;,&#8221;u&#8221;,&#8221;A&#8221;,&#8221;E&#8221;,&#8221;I&#8221;,&#8221;O&#8221;,&#8221;U&#8221;,]  
text = raw_input(&#8220;Enter text, I will remove the vowels: &#8220;)  
text_list=[]  
position=0  
for char in str(text):  
text_list.append(char)  
if char in vowels:  
text_list[position]=&#8221;&#8221;  
position=position+1  
print &#8220;&#8221;.join(text_list)

#!/usr/bin/env python  
&#8221;&#8217;  
This program will censor a given word in a given text. E.g. if the user types &#8220;This is my text!&#8221;  
and the word &#8220;text&#8221; is to be censored, the program will return &#8220;This is my \****!&#8221;  
This program is easy, but you need to make sure to censor the whole word in the text,  
and not just censor the characters that appear in the word.  
This is because there probably will be occurrences of those characters in other words that should not be censored.  
So you need to find the whole word before doing any censoring.  
&#8221;&#8217;  
text = raw_input(&#8220;Enter the text to censor: &#8220;)  
word = raw_input(&#8220;Enter the word to censor: &#8220;)  
asterisks=&#8221;&#8221;  
attemp_word=[]  
word_list=&#8221;&#8221;.join(word)  
counter=0  
for char in str(text):  
for char2 in word:  
if char == word_list[counter]:  
attemp_word.append(char)  
asterisks=asterisks+&#8221;*&#8221;  
counter=counter+1  
if &#8220;&#8221;.join(attemp_word)==word and counter == len(word):  
print text.replace(word,asterisks)  
asterisks=&#8221;&#8221;  
attemp_word=[]  
counter=0

#!/usr/bin/env python  
&#8221;&#8217;  
This program uses list comprehension to print the cubes of the numbers 1 to 10 that are evenly divisible by 4.  
&#8221;&#8217;  
cubes\_by\_four=[x\*x\*x for x in range(1,11) if ((x\*x\*x)%4 == 0)]  
print cubes\_by\_four

#!/usr/bin/env python  
&#8221;&#8217;  
This program uses list comprehension to print the squares of the numbers 1 to 10 that are even.  
&#8221;&#8217;  
even_squares=[x*x for x in range(1,12) if (x%2 == 0)]  
print even_squares

#!/usr/bin/env python  
&#8221;&#8217;  
Use list slicing to print out every odd index element of my_list (numbers from 1 to 10) from start to finish.  
Omit the start and end index. You only need to specify a stride.

Remember, the syntax for list slicing is [start:end:stride]

Since you&#8217;re using the entire list, you should leave out the start and end indices (but leave in the colons!)  
and give the slice a stride that will select every other (that is, odd) element.  
&#8221;&#8217;  
my_list=range(1,11) # List of number from 1 to 10.  
print my_list[::2]

#!/usr/bin/env python  
&#8221;&#8217;  
This one takes a list of integers as input and returns the product of all of the elements in the list.

For example: product([4, 5, 5]) should return 100 (because 4 \* 5 \* 5 is 100).

Don&#8217;t worry about the list being empty.

&#8221;&#8217;  
my\_numbers = raw\_input(&#8220;Enter the list of numbers: &#8220;)  
\# We start with the result at 1 in order to avoid a multiplication by 0.  
result=1  
for my\_number in my\_numbers:  
result = result*int(my_number)  
print &#8220;The product of your numbers is:&#8221;,result

#!/usr/bin/env python  
&#8221;&#8217;  
This one takes in a list named my_numbers, removes all odd numbers in the list, and returns the result.

For example, [1,2,3] should return [2].

This will not directly modify the list it is given as input; instead, it will return a new list with only the even numbers.  
&#8221;&#8217;  
my\_numbers = raw\_input(&#8220;Enter the list of numbers: &#8220;)  
new_list=[]  
for my\_number in my\_numbers:  
if int(my_number)%2 == 0:  
new\_list.append(my\_number)  
print new_list

#!/usr/bin/env python  
\# These are just a couple of examples of for loops.

\# Place variables into a list named &#8220;items&#8221;  
items = [&#8220;Alpha&#8221;, &#8220;Beta&#8221;, &#8220;Gamma&#8221;, &#8220;Delta&#8221;, &#8220;Epsilon&#8221;, &#8220;Omega&#8221;]

\# Lets do this in functions since were are so fancy&#8230;  
def printItems(items):  
\# Iterates over list, running statements for each item in the list  
count=0  
for item in items:  
count+=1  
\# Note: commas in print statements separate the items by a single space  
print &#8220;This is item #%s:&#8221; % count,item

def printWithFormatting(items):  
\# Iterates over list, running statements for each item in the list  
print &#8220;Now lets do it with string formatting!&#8221;  
count=0  
for item in items:  
count+=1  
\# Note: commas in print statements separate the items by a single space  
print &#8220;This is item #{0}:&#8221;.format(count),format(item)

\# Functions are called  
printItems(items)  
printWithFormatting(items)

#!/usr/bin/env python  
\# This is just an example of calling OS functions from Python.  
import subprocess  
subprocess.call(&#8220;ls -l&#8221;, shell=True)

#!/usr/bin/env python  
&#8221;&#8217;  
This one takes in a list and removes elements of the list that are the same.

For example, if the user inputs ([1,1,2,2])  
should return [1,2].

We will not remove every occurrence, since you need to keep a single occurrence of a number.  
The order in which you present your output does not matter. So returning [1,2,3] is the same as returning [3,1,2].  
Do not modify the list you take as input! Instead, return a new list.  
&#8221;&#8217;  
text = raw_input(&#8220;Enter the text to remove duplicates from: &#8220;)

&#8221;&#8217;  
We convert to a set and back into a list. Sets are collections of unique items.  
So converting our list into a set will automatically remove duplicates.  
The drawback is that, since the sets are unordered, the order will be lost.  
&#8221;&#8217;  
my_set = set(text)  
result = list(my_set)  
print result

#!/usr/bin/env python  
\# This program reverses strings. (E.g. &#8220;radar&#8221; will return &#8220;radar&#8221;)  
list1=[]  
current_position=0  
text = raw_input(&#8220;Enter your string to be reversed: &#8220;)  
for n in str(text):  
list1.append(&#8220;&#8221;)  
current_position = len(text)  
for c in text:  
list1[current_position-1]=c  
current\_position=current\_position-1  
print &#8220;Your reversed string:&#8221;,&#8221;&#8221;.join(list1)

#!/usr/bin/env python  
&#8221;&#8217;  
This thing uses a dictionary to score scrabble words.  
(I have never played scrabble, so I am not sure if this are the correct rules  
but I reckon this is the basic algorithm)  
&#8221;&#8217;  
score= {&#8220;a&#8221;:1,&#8221;b&#8221;:3,&#8221;c&#8221;:3,&#8221;d&#8221;:2,&#8221;e&#8221;:1,&#8221;f&#8221;:4,&#8221;g&#8221;:2,&#8221;h&#8221;:4,&#8221;i&#8221;:1,&#8221;j&#8221;:8,&#8221;k&#8221;:5,&#8221;l&#8221;:1,&#8221;m&#8221;:3,  
&#8220;n&#8221;:1,&#8221;o&#8221;:1,&#8221;p&#8221;:3,&#8221;q&#8221;:10,&#8221;r&#8221;:1,&#8221;s&#8221;:1,&#8221;t&#8221;:1,&#8221;u&#8221;:1,&#8221;v&#8221;:4,&#8221;x&#8221;:8,&#8221;y&#8221;:4,&#8221;z&#8221;:10}

word = raw_input(&#8220;Enter text, I will score it: &#8220;)  
word=word.lower()  
sum=0

for char in str(word):  
if char in score:  
sum=sum+score[char]  
print &#8220;Your score:&#8221;,sum