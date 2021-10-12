---
layout: post
title:  "Daisy Chain Anti-Pattern"
date:   2021-10-06 15:18:22 -0400
permalink: /daisy-chain-antipattern/
---

There's an anti-pattern that I often encounter, I call it "The Daisy Chain". Code that
follows this anti-pattern often looks neat and tidy on the surface.

# This Doesn't Seem so Bad...

{% highlight ruby %}
class ThingsController < ApplicationController
  def index
    thing_getter = ThingGetter.new
    thing_getter.get_all
  end
end
{% endhighlight %}

"Seems like a lean controller" you admit to yourself... but then you drill into `things_getter.rb`.

# The Horror

{% highlight ruby %}
class ThingGetter
  def get_all
    validate
  end

  private

  def validate
    # *validate stuff*
    log_stuff
  end

  def log_stuff
    # *log stuff*
    get_thing_a
  end

  def get_thing_a
    a = external_request_a
    get_thing_b(a)
  end

  def get_thing_b(a)
    b = external_request_b
    {things: {a: a, b: b}}
  end
end
{% endhighlight %}

:scream: :scream: :scream:

This code has problems.

- **Abstractions don't make sense**

`get_all` _does not_ in fact return "all things", it returns "validate" :man_shrugging:

- **Functions are not reusable**

It's not possible to call `log_stuff` without also calling `get_thing_a`.

- **There's Hidden Gotchas**

When you look at the controller and see `thing_getter.get_all`, you quickly assume that it's getting all the things. In reality it's doing a lot more than that.

# How To Avoid This

When code comes out as a stream of conciousness, a developer may simply make a new function when 
the prior function gets too big which results in this function "chaining" effect. Most coding I've 
done in practice has been reading & modifying code that wasn't my own. Do yourfellow developers 
a solid and consider the high-level abstractions at play and encapsulate them properly.
