---
layout: post
title:  "Migrating from Blogger to Jekyll"
date:   2022-09-18 18:19:35 -0500
# categories: jekyll update
---
I've being using [Blogger][blogger-url] for couple of years now. It is a very easy to use and a free service to start a blog. However, Blogger is limited when it comes to customizations. When I was looking for alternatives, I found out [Jekyll][jekyll-url], an open source static site generator.

Jekyll provides a fully customizable framework to write a blog using a markup language, maintain it using [GitHub][github-url] and publish using [GitHub Pages][github-pages-url]. [Jekyll Quickstart][jekyll-docs] page contains step by step instructions on how to create a Jekyll site and run it locally.

Once you have the site running locally, you are ready to migrate your blog from Blogger to the new Jekyll site. Follow the export and import steps below:

#### Exporting your blog from Blogger

Sign in to your Blogger dashboard, go to `Settings > Manage blog > Back up content`. You will be able to download the back up `blog-MM-DD-YYYY.xml` file from there.  

#### Importing your blog to Jekyll

Once you have the `blog-MM-DD-YYYY.xml` file, you'll need to install `jekyll-import` ruby gem using the following command:

``` shell
$ gem install jekyll-import
```

Then run the following:

``` shell
$ ruby -r rubygems -e 'require "jekyll-import";
    JekyllImport::Importers::Blogger.run({
      "source"                => "/path/to/blog-MM-DD-YYYY.xml",
      "no-blogger-info"       => false, # not to leave blogger-URL info (id and old URL) in the front matter
      "replace-internal-link" => false, # replace internal links using the post_url liquid tag.
    })'
```
That is it! Now you have all your blogs from Blogger under the `_posts` directory on your Jekyll project.

**References,**\
<https://import.jekyllrb.com/docs/installation>\
<https://import.jekyllrb.com/docs/blogger>\
<https://support.google.com/blogger/answer/41387?visit_id=638007642044806946-20678644&rd=1>


[blogger-url]: https://www.blogger.com
[jekyll-url]: https://jekyllrb.com
[jekyll-docs]: https://jekyllrb.com/docs
[github-url]: https://github.com
[github-pages-url]: https://pages.github.com