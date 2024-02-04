---
title: "Create a blog for free with Jekyll and Github Pages"
date: 2024-01-28 16:14:00 +0100
categories: [Web]
tags: [jekyll, ruby, static, site, generator, github, pages, guide, learning, setup, programming]
---

Have you ever thought about starting a blog that transforms your ideas into something helpful for everyone,
but put the idea away because of the amount of work it takes for hosting your page and all the tedious backend
solutions?

Don't be afraid! With the *Ruby* Framework **Jekyll** for site generation and free hosting possibilities like
*Github Pages* there is no need for a backend or a complex knowledge in web development.

I share with you some interesting starting points, that should lead you to a quick, easy and free start with your 
blog post or personal page.

## Getting started with Jekyll
*Jekyll* is a static site generator that uses *Ruby* scripts with *Ruby* 2.5.0 or higher. You can even start a server that hosts
your page.

The main element of a Jekyll project is the *__config.yml* file for customizing variables, templates and other building related 
settings.

The other core concepts are the HTML and Markdown files inside the specific folders. As default Jekyll creates 
blog posts when you store Markdown files with the syntax ```yyyy-mm-ddd-title.md``` in the folder *_posts*.
This makes it easy to have a quick start with less boilerplate code.

Please refer to the _[Quickstart](https://jekyllrb.com/docs/)_ guide.

## Themes
Having a quick with Jekyll is fine, but creating a blog site still costs a lot of time. The content structure needs optimization and
should look good on every device. 

Here comes one very strong feature of *Jekyll* and that is theming. In the *_config.yml* you can reference a theme from a provider
of your choice, so you have a strong foundation for your new blog. On  _[Jekyll Theme](https://github.com/topics/jekyll-theme)_ you
can find a theme for
every style or topic that you can think of. Most creators also have some additional information on specific configurations.

## Github hosting
The good thing about hosting with *Github Pages* is that it uses *Jekyll* as a default site generator engine. You just need to
add a ```pages-deploy.yml``` file with some basic configurations under the *.github/workflows* folder inside the root of your project.
A complete tutorial from the official *Github* Site can be found under
_[Setting up a Github Pages Site with Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll)_.

When you name your repository *\<username\>.github.io* and set the visibility to public, than the hosting even is **for free**.

## Special Thanks
Thanks to _[@TechnoTim](https://www.youtube.com/@TechnoTim)_ for the helpful tutorial on getting started with Jekyll themes
and to _[Cotes](https://github.com/cotes2020)_ for the _[Chirpy Theme](https://github.com/cotes2020/jekyll-theme-chirpy)_ that 
powers this blog.