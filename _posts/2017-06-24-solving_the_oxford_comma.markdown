---
layout: post
title:  "Ruby - Solving the Oxford Comma"
date:   2017-06-24 22:17:18 -0400
---

So yesterday I spent several hours racking my brain and researching different ways to turn an `array` of items (i.e. `["peaches", "grapes", "oranges", "pineapple", "passion fruit"]`) into a comma seperated `string` with the word "and" before the last item: `"peaches, grapes, oranges, pineapple, and passion fruit"`.

Finally I came up with this:

```array.insert(-2, "and").join(", ").sub("and,", "and")```

But lets break down how this works and why.

Call `.insert(-2, "and")` on `array`. We pass two arguments to the `.insert` method - the index number and what you want to insert. In this case: `-2` and `"and"`, and using them to insert `and` into the array at the `-2` index. Negative numbers for the index start at the end of the array and work backwards toward the beginning. So in the example array above that would return a new array:

```["peaches", "grapes", "oranges", "pineapple", "and", "passion fruit"]```

We then call `.join(", ")` on the new array which turns the array into a string with a comma and a space after every item. This results in the following string:

```"peaches, grapes, oranges, pineapple, and, passion fruit"```

As you can see we have a slight problem. There is a comma after the word `and`. In order to get rid of it we then call `.sub("and,", "and")` which searches the string for `and,` and changes it to `and`. Resulting in the completed string:

```"peaches, grapes, oranges, pineapple, and passion fruit"```
