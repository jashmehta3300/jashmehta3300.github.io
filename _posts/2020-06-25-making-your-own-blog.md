---
title: Installing Jekyll on Windows and setting up your own blog!
date: 2020-06-25 
permalinks: /posts/2020-6-25-making-your-own-blog
toc: true
excerpt_separator: <!--more-->
tags: 
  - Tech
---

This post is a step-by-step guide for making your own blog within minutes!

<!--more-->

After reading a lot of elusive and poorly documented docs, I finally figured out how to set up the [Hyde](https://hyde.getpoole.com/){:target="_blank" rel="noopener"} theme and modify it to suite my needs. The previous blog site I used was made using the same theme. This one is made using [Jasper](https://github.com/jekyller/jasper2){:target="_blank" rel="noopener"} which is similar to Hyde. I hope this post helps you in setting up your own blog within minutes.

Before we start, I just want to share a couple of blogs I love reading which made use of the same theme. It is very flexible and easily customizable. 

* [Anish Athalye's blog](https://www.anishathalye.com/){:target="_blank" rel="noopener"}
* [Rachel Thomas's blog](https://www.fast.ai/topics/){:target="_blank" rel="noopener"}

We will use Jekyll. [Jekyll](http://jekyllrb.com){:target="_blank" rel="noopener"} is a static site generator, an open-source tool for creating simple yet powerful websites of all shapes and sizes. From [the project's readme](https://github.com/mojombo/jekyll/blob/master/README.markdown){:target="_blank" rel="noopener"}:

  > Jekyll is a simple, blog aware, static site generator. It takes a template directory [...] and spits out a complete, static website suitable for serving with Apache or your favorite web server. This is also the engine behind GitHub Pages, which you can use to host your project’s page or blog right here from GitHub.

Without wasting more time, let's get started! 

## Step 1 - Install Ruby and the Ruby DevKit

Ruby is the programming language that Jekyll is written in. You’ll need to install Ruby and the corresponding DevKit, which is needed to build some of Jekyll’s dependencies as native extensions.

<p class="message">
  <strong>Ruby is pre-installed on Mac and most Linux distributions by default.</strong> However, the pre-installed version is a few versions behind so we'll look into the other ways to install Ruby.
  <br>
  Windows users have a bit more work to do.
</p>
Click [here](https://images.app.goo.gl/Hi34vanYdnD988UY8){:target="_blank" rel="noopener"} to see Torvalds thoughts on Windows (sorry, couldn't resist :p) 

<br>

* To install the latest version of Ruby on linux, click [here](https://www.thoughtco.com/instal-ruby-on-linux-2908370#:~:text=Ruby%20is%20installed%20on%20most,interpreter%20on%20your%20Linux%20compute){:target="_blank" rel="noopener"}

* To install the latest version of Ruby on Mac, click [here](https://stackify.com/install-ruby-on-your-mac-everything-you-need-to-get-going/){:target="_blank" rel="noopener"}

<br>

Now, for windows, follow this procedure.

Since, using Jekyll on Windows is not officially supported by the Jekyll team, the procedure is a somewhat abstruse but I have tried by best to expound it. 

First, click [here](https://rubyinstaller.org/downloads/){:target="_blank" rel="noopener"} and download the installer for Ruby v2.6.6-1 that matches your system’s architecture (x86 / x64).

You can download it anywhere on your computer.Due to memory issues in my C drive, I have downloaded it in the D drive. 

<p align="center" class="images">
<img src="assets/images/Capture2.JPG" />
</p>

Execute the installer and go through the steps of the installation. When you get to the screen below, make sure to check the “Add Ruby executables to your PATH” box.

Click Install and Ruby will be installed within seconds.

<p align="center" class="images">
<img src="assets/images/Capture1.JPG" />
</p>

After the installation is done, you will see this in you command prompt. Select option ```3``` and hit enter.

<p align="center" class="images">
<img src="assets/images/Capture3.JPG" />
</p>

Once the downloading is done, it will again ask you to select an option. This time just hit enter without giving an input.

<strong>Note:</strong> You need to restart your terminal before trying the following steps.

<br>

## Step 2 - Install Jekyll

Jekyll itself comes in the form of a Ruby Gem, which is an easy-to-install software package. To install Jekyll and all its default dependencies, launch your favorite command line tool and enter the following command.

```
  gem install jekyll
```

Hit enter, watch, enjoy. This might take a while due to the number of dependencies.

The latest version of Jekyll at the time of writing is v4.1.1, which is compatible with Windows. Most of the previous versions are, too. Do not attempt to install Jekyll v1.4.3, though, which is [known to be incompatible with Windows](https://github.com/jekyll/jekyll/issues/1948){:target="_blank" rel="noopener"}.

<br>

## Step 3 - Clone the Hyde repository 

```
mkdir my-blog
cd my-blog
git clone https://github.com/poole/hyde.git
cd hyde
```

<br>

## Step 4 - Making some changes in the cloned files

Before running, we will make a few changes in your code to avoid errors.

* The permalinks are deprecated in version 3 - we can remove a line ```relative_permalinks: true``` from _config.yml and add this in the end of the file:

```
plugins:
  - jekyll-paginate
  - jekyll-gist
  - redcarpet
```

* We will now edit the line ```markdown: kramdown``` in _config.yml

After making sure that you are inside the ```hyde``` directory, run: 

```
gem install jekyll-paginate jekyll-gist redcarpet
jekyll serve
```

* Now, change the personal details in the _config.yml file. Specially change the ```url: https://<your-username>.github.io``` and ```baseurl: /```

* Go to the head.html file inside the _includes folder. Remove lines 17 to 25 (ie. the 4 link tags under CSS and 2 under Icons) and instead, copy paste this: 

```
  <!-- CSS -->
  <link rel="stylesheet" href="/public/css/poole.css">
  <link rel="stylesheet" href="/public/css/syntax.css">
  <link rel="stylesheet" href="/public/css/hyde.css">
  <link rel="stylesheet" href="http://fonts.googleapis.com/css?family=PT+Sans:400,400italic,700|Abril+Fatface">

  <!-- Icons -->
  <link rel="apple-touch-icon-precomposed" sizes="144x144" href="/public/apple-touch-icon-144-precomposed.png">
  <link rel="shortcut icon" href="/public/favicon.ico">
```

Open ```http://localhost:4000``` to see your blog site.

<br>

## Step 5 - Hosting the blog on ```gh-pages``` for free

We will now host your blog on the internet with the help of Github.

* Make a repository on Github with the name: ```<your-username>.github.io```
* Push your code on this repository using the following commands: 

```
git add .
git commit -m "initial commit"
git remote add origin https://github.com/<your-username>/<your-username>.github.io.git
git push origin master
```

* Go to ```Settings``` on Github and you'll see that your website is hosted !!!

<p align="center" class="images">
<img srcset="assets/images/Capture4.JPG 2w" sizes="1px" />
</p>

<strong>DONE!</strong> Now you can make changes according to your requirements. 

<br>

Thankyou for reading! 
