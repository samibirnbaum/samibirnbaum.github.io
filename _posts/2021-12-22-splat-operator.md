---
layout: post
title: Ruby Splat Operator 🌟
---

The splat operator is confusing and here is why...

<!--more-->

It does 2 things that are the exact opposite of each other.

Let me explain...

It destructures an array, which looks something like this:

{% highlight ruby %}

x, y, z = [1,2,3]

puts x 
# => 1

puts y 
# => 2

puts z 
# => 3

{% endhighlight %}

But it can also be used to construct an array:

{% highlight ruby %}

x = *123
#=> [123]

{% endhighlight %}

If you think about this, it is doing two very different things.

One takes an array and **removes** the surrounding [].

`[123]` becomes `123`

The other takes a value and **adds** the surrounding [].

`*123` becomes `[123]`.

The only question we need to answer then is when does it destruct and when does it construct? 🤔

If you use it when **defining a method** it will take any argument you give it and **construct** it into an array.

{% highlight ruby %}

def do_a_thing(*args)
  puts args
  puts args.class
end

do_a_thing(1,2,3)
# 1
# 2
# 3
# Array

{% endhighlight %}

If you use it when **passing arguments as an array to a method** it will **deconstruct** the array into arguments.

{% highlight ruby %}

def do_a_thing(x,y,z)
  puts x
  puts x.class
end

do_a_thing(*[1,2,3])
# 1
# Integer

{% endhighlight %}

Hopefully now we can understand code that looks like this:

{% highlight ruby %}

class Thing
  def self.perform(*args) # this splat operator will construct any arguments into an array
    new(*args).perform # this splat operator will deconstruct that array into arguments 
  end
  
  def initialize(x,y,z)
    @x = x
    @y = y
    @z = z
  end
  
  def perform
   puts @x
  end
end

Thing.perform(1,2,3)
# => 1

{% endhighlight %}

_As an aside, the reason for the above class method of `perform`, is so you can easily call
`Thing.perform()`, without having to first instantiate the object._

_Using `*args` means that if our expected parameters in the `initialize` method were to change
we would never have to change them in the `perform` class method._

******************************

Credit to [this article](https://www.honeybadger.io/blog/ruby-splat-array-manipulation-destructuring/) which helped to shape my understanding.
