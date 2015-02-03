---
layout: post
title: Python's zip, map, and lambda
tags: ['python', 'code']
---
<p class="lead">A simple explanation</p>

Let us assume that we have got *a* and *b*: two lists of integers. The goal is to merge them into one list, keeping whichever value is the largest at each index.

{% highlight python  %}
>> a = [1, 2, 3, 4, 5]
>> b = [2, 2, 9, 0, 9]
{% endhighlight %}

We can write a simple function that compares each item from a and b, then stores the largest in a new list as shown below:
{% highlight python linenos %}
def pick_the_largest(a, b):
    result = []  # A list of the largest values
    # Assume both lists are the same length
    list_length = len(a)
    for i in range(list_length):
        result.append(max(a[i], b[i]))
    return result
{% endhighlight %}

however the pythonic way to write is by a single line !
{% highlight python  %}
>> map(lambda pair: max(pair), zip(a, b))
[2, 2, 9, 4, 9]
{% endhighlight %}

Let us understand these functions one by one,

### Zip
[zip](http://bit.ly/python-zip) function takes two equal-length collections, and merges them together in pairs. If we use this on our a and b, we get,
{% highlight python  %}
>>> zip(a, b)
[
    (1, 2),
    (2, 2),
    (3, 9),
    (4, 0),
    (5, 9)
]
{% endhighlight %}

### Lambda
[lambda](http://bit.ly/python-lambdas) is a shorthand to create an anonymous function. It's often used to create a one-off function (usually for scenarios when you need to pass a function as a parameter into another function). It can take a parameter, and it returns the value of an expression.

Now, assuming that we have a a pair of values, we can create a function that picks the larger of the pair:

{% highlight python  %}
>>> lambda pair: max(pair)
{% endhighlight %}

### Map

[map](http://bit.ly/python-map) takes a function, and applies it to each item in an iterable (such as a list).
Thus putting it all together we get the single line pythonic solution,
{% highlight python  %}
>>> map(  # apply the lambda to each item in the zipped list
        lambda pair: max(pair),  # pick the larger of the pair
        zip(a, b)  # create a list of tuples
    )
[2, 2, 9, 4, 9]
{% endhighlight %}

This example originally appeared [here](https://bradmontgomery.net/blog/2013/04/01/pythons-zip-map-and-lambda/)
