---
layout: post
title: How to Make a Blog
date: 2020-11-09 5:30:00 -0800
description: This post describes how to make a blog using Jekyll and Github Pages # Add post description (optional)
img: making-a-blog.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Blog, Writing]
---

I work on a variety of projects and write copious notes and documentation along the way but never quite make it to the final step of documenting the final products. I've attempted to create blogs on many different platforms with varying levels of cost and complexity, but I've always come back to using static site generators.

## Types of Blogs:

I won't go into great detail here but it's worth mentioning the benefits and drawbacks of static site generators (SSG) like Jekyll over full Content Management Systems (CMS) like Wordpress. For simplicity you can view a static site generator as a happy medium between the basic html pages you created as your web site in your high school tech class and a full managed website with databases, servers and the sorts. 

This is a general pros and cons list of using Jekyll + Github Pages over something like Wordpress with a web host:

### Static Site Generator Pros

- Free
- Simple / Lightweight
- Integrates with Github

### Static Site Generator Cons

- Simple/Limited options for plugins
- Potential SEO limitations
- Lacks an admin page - requires more manual management

### Content Management System Pros

- Lots of Support/Plugins
- Easy / WYSIWYG
- SEO
- Administration panels

### Content Management System Cons

- Cost Money
- Subject to 3rd parties
- Can be bloated

Both options are good, it's really just a matter of what platform will fit the best for what you are trying to accomplish. I personally see static site generators used more in the technical world with portfolios and tech blogs. I use Github regularly for projects so it makes sense for me to use Jekyll with Github Pages. 

## Creating this Blog

One of the simplest ways to create a blog is to use a Jekyll theme that someone already created and then modify and add your own content to make it your own. You can create and manage everything directly through the Github web interface but I find it easier to test and troubleshoot locally on my computer before pushing to my Github repository. 

### Installing Jekyll:

This is assuming an ubuntu based linux distro

Dependencies

```
sudo apt-get install ruby-full build-essential zlib1g-dev
```

Jekyll

```
sudo gem install jekyll bundler
sudo gem install jekyll-sitemap
sudo gem install jekyll-paginate
sudo gem install jemoji
```

### Using Jekyll

I am using the flexible-jekyll theme by Artem Sheludko

you can fork and download the content like so:

```
git clone https://github.com/artemsheludko/flexible-jekyll.git
```

go into working directory:

```
cd flexible-jekyll
```

Compile Pages:

```
jekyll serve
```

It will give you a local host URL to access your local build, which in my case was the following: 

http://127.0.0.1:4000/flexible-jekyll/

To cancel the jekyll server just press `ctrl+c`

## Customizing the Page

The default file for customizing the main page is the `_config.yml`

This is the default page:

```yaml
title: Hello, world! I'm David Freeman
description: > # this means to ignore newlines until "baseurl:"
  Write an awesome description for your new site here. You can edit this
  line in _config.yml. It will appear in your document head meta (for
  Google search results) and in your feed.xml site description.
permalink: ':title/'
baseurl: "/flexible-jekyll" # the subpath of your site, e.g. /blog
url: "" # the base hostname & protocol for your site, e.g. http://example.com
site-twitter: #if your site has a twitter account, enter it here

# Author Settings
author: David Freeman # add your name
author-img: david-freeman.jpg # add your photo
about-author: I am a web developer focusing on front-end development. Always hungry to keep learning. # add description
social-twitter: # add your Twitter handle
social-facebook: # add your Facebook handle
social-github: artemsheludko # add your Github handle
social-linkedin: # add your Linkedin handle
social-email: # add your Email address

# Disqus
discus-identifier: mr-brown # add your discus identifier

# Tracker
analytics: # Google Analytics

# Build Settings
markdown: kramdown
plugins:
  - jekyll-sitemap
  - jekyll-paginate
  - jemoji

paginate: 8
paginate_path: "/page/:num"

exclude: ["node_modules", "gulpfile.js", "package.json", "yarn.lock"]
```

You can switch out the relevant fields and add your own images and favicons under `flexible-jekyll/assets/img/` and `flexible-jekyll/assets/img/favicon/`

## Adding Posts

To create a post you'll need to create a `.markdown` file in `flexible-jekyll/assets/posts/`

The filename should have the pattern `YYYY-MM-DD-post-title.markdown` eg `2020-11-09-making-a-blog.markdown`

The general header looks like this:

```yaml
---
layout: post
title: How to Make a Blog
date: 2020-11-09 5:30:00 +0800
description: This post describes how to make a blog using Jekyll and Github Pages # Add post description (optional)
img: making-a-blog.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Blog, Writing]
---
```

As above you'll want to put any image assets in `flexible-jekyll/assets/img/`. All that's left is to fill the body with content using the markdown format and save the markdown file and you've finished your first post. 

## Publishing to Github

Github is fairly flexible in how you publish your static page. Assuming you don't have a custom domain, you can rename the `flexible-jekyll` repo name to your `githubhandle.github.io` and just set the `config_yml` baseurl to `baseurl: "/"`. If you have an existing domain you want to use you can use you can set it in your github repo settings and set the baseurl to `/blog` or whatever you like.

Github will publish your page from the master or master/docs or you can put it under a different branch called gh-pages. There isn't a specific advantage to publishing in master vs a branch other than just how you want to organize your workflow. I generally like to separate the original fork from my changes and just cherry pick any updates but some people prefer to work directly off the master fork and thats fine too. 

To publish to the master, once you've cloned and made your changes to your theme, these are the commands I use in the terminal:

```shell
git add -A
git commit -m "Initial Commits"
git push origin master
```
If everything goes according to plan your site will shortly show up at the domain you configured, which in my case is [https://anthonyblackham.github.io/blog/](https://anthonyblackham.github.io/blog/)

### Summary

This is just the basic getting started tutorial but there are plenty of other options to tweak and modify the blog to make it unique and provide a platform that will showcase everything that you have to offer to the world.

