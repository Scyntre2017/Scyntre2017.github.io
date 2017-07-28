---
layout: post
title:  "Ruby - Iterating Through Iterators: #Each"
date:   2017-07-28 01:13:17 +0000
---

At the beginning of my venture into programming, I started out learning Ruby, and I was introduced to the concept of iterators fairly early on (an iterator is a block of code that allows you to manipulate any or all data points in a set of data). I found them to be easy to grasp conceptually, but when I tried to put them into practice I spent hours figuring out how to use them. Even after using them, I still sometimes didn't understand how they worked. Thus, in an effort to better my own understanding and hopefully help out others who struggle with them too, I am going to try to write a blog post on each iterator.

There are many classes that iterators work with, but because I don't understand all of the classes in Ruby yet, in these posts I am only going to include the ones that I do. I will try to update these posts as my knowledge base in Ruby expands.

The most basic iterator is the `#each` method, which basically does exactly what it says - goes through each data point and does whatever you specify with it.

**Using #Each with the Array class**

```a = [1, 2, 3, 4, 5]
a.each do { |x| puts x }```

This loops through the array `[1, 2, 3, 4, 5]` and assigns each value to `x` and then does something with `x` on each loop. This allows you to print out the numbers in the array to the screen:

```1
2
3
4
5```

**Using #Each with the Hash class**

```b = {first: "a", second: "b", third: "c", fourth: "d", fifth: "e"}
b.each { |key, value| puts "#{key}: #{value}" }```

This loops through the hash `{first: "a", second: "b", third: "c", fourth: "d", fifth: "e"}` and assigns each key to `key` and each value to `value` and then does something with each `key` and `value` on each loop. This allows you to print out the hash keys and values to the screen:

```first: a
second: b
third: c
fourth: d
fifth: e```

**Using #Each with the Range class**

```c = (1..9)
c.each { |x| puts x + 1 }```

This loops through the numbers in the range `(1..9)` and assigns each number to `x` and then does something with `x` on each loop. This allows you to print the numbers in the range to the screen plus one:

```2
3
4
5
6
7
8
9
10```

**Conclusions**

This all seems pretty standard. The `#each` method is working exactly like expected. You then try to implement it into your code only to discover that you aren't getting back the values you expected. The problem is that the `#each` method's return value is the original set of data. So in the examples above the Array's return value is `[1, 2, 3, 4, 5]`, the Hash's return value is `{first: "a", second: "b", third: "c", fourth: "d", fifth: "e"}`, and the Range's return value is `(1..9)`. You say, "But that's because you used `puts`, of course it isn't going to return anything different. Ah, my friend, but that's where you are wrong, if it was working exactly like you expected it would return `nil`. (That is, at least, what I was confused by when I was learning it.) Even if you took out `puts` and did something else with each point of data it would still return the original set of data.

So how do you get other values out of the `#each` method? You have to set a variable outside of `#each` and then change it based on each point of data within `#each`.

Let's look at a few examples.

Let's say I want to check if `[ "O", "X", " ", " ", " ", "X", "O", " ", "X"]` is full of X's and O's.

```a = [ "O", "X", " ", " ", " ", "X", "O", " ", " "]
value = nil
a.each do |x|
  if x == " "
	value = false
	else
	values ||= true
end
value => false```

I first set `value` equal to `nil` and then change it based on each point of data. So the first `" "` the `#each` method encounters sets `value` equal to `false` and then only changes it to `true` if it wasn't previously set to `false`. The `x ||= a` is basically an easy way of saying if `x` isn't equal to something (other than `nil`) set it equal to `a` if it already is equal to anything except `nil` thend don't set it equal to `a`.

What if I want to add the value of the range `(1..9)`?

```a = (1..9)
sum = 0
a.each do |x|
  sum = sum + x
end
sum => 45```

I first set `sum` equal to `0`. Then on each loop of `#each` I add the value of the number of that loop. Coming up with the sum of 45.

I hope you have found these examples helpful and if you have any questions, feel free to contact me.
