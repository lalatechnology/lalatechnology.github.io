---
layout: post
title:  "Create Github Pages"
date:   2021-04-21 10:20:30 -0000
categories: static web development
---

### TL;DR

What is the simplest, easiest and fastest way to create Static Web Site?

First I thought it could Word Press, but I found myself drowned in a see of pages to setup different parts of the site. I am not new to web development, but found it a bit overwhelming to navigate through bunch of property screens.

Frustrated, I jumped searched Google and of course there were plenty of advices from all over the world. Everybody have their favorite way of develping web sites. One thing cought my attention: quite a bit of people were talking about github pages. I decided to give it a try.

After going through Github [documentation](https://docs.github.com/en/pages), Github Pages boils down to a few concepts:

1. You can put your code into Github repo, configure settings and your code will be automatically published.
2. Github uses [Jekyll](https://jekyllrb.com/docs/github-pages/) generator to build static web site.
3. You can use your own code structure, but it probably better to comply with the structure Jekyll recommends/supports.
4. All themes have default code, but you can overwrite and customize it by copying it into your repo and modifying the code.
5. There are a lot of 3rd party themes and componenets you can add you your code, but I consider that a suger on a cake. You can pick up the theme you like, but I wouldn't go further than that, at least not at the beginning.

Let's take a look at each of this concepts in details and follow the process step-by-step untill we have a static site up and running. 

I have spent some time reading the docs. It is nice to take a look at them as a reference when you have questions, but I hope I can save you some time by just guitding through basic steps. I will point out to the docs where repeating them woin't make sense. My goal is to guide through the process and point to the pitfalls.
 
### Step 1. Create Github Repo




It probably will have some code snippets like this:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}
