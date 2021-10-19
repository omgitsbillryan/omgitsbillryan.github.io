---
layout: post
title:  "Versioning External Dependencies"
date:   2021-10-11 22:17:00 -0400
permalink: /versioning-your-dependencies/
---

## What Happened

I recently encountered an outaged caused by an external library called `github-exporter`.
The library was used to track a few simple metrics about GitHub usage. The ansible code 
looked something like this:

{% highlight yaml %}
- name: Install github-exporter
  docker_container:
    image: infinityworks/github-exporter:latest
{% endhighlight %}

This worked great for about a year and then one afternoon... :boom:. 
Suddenly, the 5,000 GitHub API hourly quota was being eaten up inside 5 minutes!

## The Root Cause

A new image of `infinityworks/github-exporter` was released to dockerhub. The
new version changed the default GitHub API pagination behavior. Since the version
was set to `:latest`, ansible happily consumed & deployed the latest docker image.

## Versioning Options

Using `:latest` is clearly not suited for production-level 
software where stability is paramount. The strictest option would be to use
a git commit SHA, e.g. 
```
infinityworks/github-exporter@sha256:46e0c757cfcea569501c77ba7e6f72c80123e2a4
```
This has it's own tradeoff as you're no longer receiving potential security patches
for free. The middleground is to use a tag name like so,
````
infinityworks/github-exporter:1.0.2
```
Keep in mind that it's still possible for [new commits to be made to the underlying
git code w/o the dockerhub image version changing](https://rockbag.medium.com/why-you-should-pin-your-docker-images-with-sha-instead-of-tags-fd132443b8a6), so it's
not exactly a silver bullet.

## Closing Thoughts

In the end, it's up to you the developer to chose the proper version for your given
situation - choose wisely.