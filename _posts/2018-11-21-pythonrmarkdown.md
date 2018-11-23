---
title: "Python code chunks in R Markdown"
author: "Michael Knous"
date: "November 21, 2018"
output: html_document
---




## A normal R Code Chunk


{% highlight r %}
x=42
print(x)
{% endhighlight %}



{% highlight text %}
## [1] 42
{% endhighlight %}

## modify an R variable

In the following chunk, the value of `x` on the right hand side is 42, which was defined in the previous chunk


{% highlight r %}
x = x+12
print(x)
{% endhighlight %}



{% highlight text %}
## [1] 54
{% endhighlight %}

## A python chunk

This works fine and as expected


{% highlight python %}
x = 42*2
print(x)
{% endhighlight %}

{% highlight text %}
## 84
{% endhighlight %}

The value of `x` in the Python session is 84.
It is not the same `x` as the one in R.

## Modify a Python variable


{% highlight python %}
x = x + 18
print(x)
{% endhighlight %}



{% highlight text %}
## 102
{% endhighlight %}

Retrieve the value of `x` from the Python session again:


{% highlight r %}
py$x
{% endhighlight %}



{% highlight text %}
## [1] 102
{% endhighlight %}

Assign to a variable in the Python session from R:


{% highlight r %}
py$y = 1:5
{% endhighlight %}

See the value of `y` in the Python session:


{% highlight python %}
print(y)
{% endhighlight %}



{% highlight text %}
## [1, 2, 3, 4, 5]
{% endhighlight %}

##Python graphics

You can draw plots using the **matplotlib** package in Python.


{% highlight python %}
import matplotlib.pyplot as plt
plt.plot([0,2,1,4])
plt.show()
{% endhighlight %}

![plot of chunk unnamed-chunk-8](/assets/Rfig/unnamed-chunk-8-1.svg)


{% highlight python %}
import sys
print(sys.version)
{% endhighlight %}

Please note that in RStudio, variables generated in python code chunks are not shared between code chunks.  They however will shared between code chunks in the knitr generated documents.