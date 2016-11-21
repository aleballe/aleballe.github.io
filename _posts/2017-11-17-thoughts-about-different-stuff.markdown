---
title:  "Thoughts about different stuff"
description: Some thoughs about CSS preprocessors, static site generators, robots.txt, humans.txt and open graph.
date:   2017-11-17
categories: css
img: the-matrix.jpg
---
## CSS preprocessors

Initially when hearing about the CSS preprocessors I was a little bit put off. Yet another tool I have to learn? More dependencies that
will screw up everything? Turns out CSS preprocessor languages such as `SASS` or `LESS` isn't so bad after all.

I'm not going to walk you through the installation process, there's a good resource for that [here][sass-resource]. I have only
worked with SASS for the better part of of an afternoon but can already see the great value it provides even though I'm not working on
a huge project.

`SCSS` and `SASS` are supposedly the same thing, just different syntaxes. I've been using SCSS so that's what you're going to see in the example below which illustrates some good stuff about SCSS I so far have learnt.

### Variables

Here's an example of what you can do with SCSS:

{% highlight SCSS %}
$cool-color: #ef99ba;

.header {
    color: $cool-color;
}

a:hover {
    color: $cool-color;
}
{% endhighlight %}

The color `#ef99ba` is stored in the variable `$cool-color` which is used instead of actually typing the color manually each time. This is one problem with CSS that SCSS/SASS remedies in a way that more reminds of how programming languages works.

### Nesting

Nesting is arguably more intuitive than the traditional way of writing CSS. Let's make a comparison. This is how you maybe would style a navigation with classical CSS:

{% highlight CSS %}
nav {
    background-color: blue;
}

nav ul {
    list-style: none;
}

nav li {
    display: inline-block;
}

nav a {
    color: green;
}
{% endhighlight %}

With SCSS it looks something like this instead:

{% highlight SCSS %}
nav {
    background-color: blue;

    ul {
        list-style: none;
    }

    li {
        display: inline-block;
    }

    a {
        color: green;
    }
}
{% endhighlight %}

A bit more intuitive and easy to understand I would say.

### Partials

SCSS let's you structure your stylesheets into separate files by dividing them into `partials`. These partials are imported with the `@import` directive like so:

{% highlight SCSS %}
// Other SCSS in the main SCSS file

// The partials
@import "partials/square";
@import "partials/triangle";
@import "partials/circle";
{% endhighlight %}

The impressing thing is that all these SCSS files are combined into one CSS file through the pre-compiling process.

## Static site generators

This site is actually built with a static site generator called `Jekyll`. Just like with SCSS this means there's another tool to learn and master, but it's been a quite intuitive and nice experience. Perfect if you're going to build a static site and want the dynamic
properties of a site built with for example `PHP`.

Static site generators are suitable for sites that won't change so much over time and which aren't gigantic, but if you're building something like a portfolio website this is a lightweight, secure and fast alternative.

## Robots.txt

The `robots.txt` file is a way to give instructions to web robots that crawl the web about which pages and directories they should crawl.
I simply wrote `User-agent: *` in mine meaning that all all web robots are welcome to crawl.

## Humans.txt

the `humans.txt` file is a way of knowing the people behind a website. It's like robots.txt, but for humans. I implemented it by creating a humans.txt file which I put into the root directory of the website just like with robots.txt.

## Comments on this site

I used `Disqus` to get a comment section on my posts. It was a quite straightforward process, I simply followed their guide on how to install [Disqus on Jekyll][disqus-guide].

Basically I created an account at their website and then I got some code to copy and paste into desired position. The code was then wrapped by a condition checking if it should display the comment section or not. I sat the condition to be true in the post layout so all files using the post layout would have a comment section.

## Open Graph

`Open Graph` is a way of talking control of how a webpage is presented when shared. There a many different `og-tags` to choose from, I made use of the following:

* og:title
* og:description
* og:url
* og:image

The way to use them is to include them in the `head` section, it might look like this:

{% highlight HTML %}
<head>
// Other stuff in the head section

<meta property="og:title" content="Bob" />
<meta property="og:description" content="Bob is a nice person." />
<meta property="og:url" content="http://www.bob.com" />
<meta property="og:image" content="http://www.bob.com/images/bob.jpg" />

</head>
{% endhighlight %}

[sass-resource]:      http://sass-lang.com/install
[disqus-guide]:       https://help.disqus.com/customer/portal/articles/472138-jekyll-installation-instructions
