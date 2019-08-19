---
layout: post
title: "Set up blog tools: Jekyll and Atom"
date: "2017-12-21 07:58"
---
**Contents**
	- [Introduction](#introduction)
	- [Install Atom](#install-atom)
	- [Install Jekyll dependencies](#install-jekyll-dependencies)
		- [Opening and understanding the Terminal](#opening-and-understanding-the-terminal)
		- [Install Xcode and its Command Line Tool](#install-xcode-and-its-command-line-tool)
		- [Install Homebrew](#install-homebrew)
		- [Install Ruby Version Manger (RVM)](#install-ruby-version-manger-rvm)
		- [Install Ruby](#install-ruby)
	- [Install Jekyll](#install-jekyll)
		- [Edit the configuration (\_config.yml)](#edit-the-configuration-configyml)
		- [Cusomized CSS](#cusomized-css)
			- [Extending the CSS](#extending-the-css)
			- [Customised \_includes](#customised-includes)
		- [Writing this blog post](#writing-this-blog-post)
	- [Next blog (Setup GitHub pages)](#next-blog-setup-github-pages)
	- [Resources](#resources)

## Introduction

This blog post is for remembering how I set up the tools for writing my own blog posts.

After looking at different alternatives, I decided to try [Jekyll](https://jekyllrb.com) that is available from [GitHub](https://github.com). A main reason is that it relies more on coding and less on graphical interfaces. And that is how I am used to work with Geo Imagine and writing my scientific texts.

Jekyll expects a ['markdown'](https://daringfireball.net/projects/markdown) file for each blog, and I needed to find a text editor that facilitates generating markdown text files. Browsing different alternatives I settled for [Atom](https://atom.io). Atom is advertised as 'A hackable text editor', and it resembles the text editor (TeXShop) that I use for scientific writing.

This blog covers the installation and setup of Jekyll and Atom on a local machine, and generating a web page on your local machine. The [next blog](https://karttur.github.io/setup-github/index.html) covers a bit more about organizing a Jekyll site, and how to publish Jekyll sites to GitHub.com. And then a [third blog](https://karttur.github.io/setup-theme-blog/index.html) is about using a more rich template Theme for Jekyll. The three blogs are available in different repositories on [GitHub.com](https://github.com). They are on different sites because they use different Jekyll setups.

If you want to download the complete Jekyll setup for this blog it is available as a [GitHub repository](https://github.com/karttur/setup-blog/tree/gh-pages).

## Install Atom
[//]: # (https://discountry.github.io/2017/02/15/use-atom-as-your-markdown-editor/)
Installing Atom is much simpler than installing Jekyll, and you will also need Atom for some text editing for creating your blog. So let us start with installing Atom.

For macOS, Atom is available as a disk image, and is installed by [downloading](https://atom.io), and opening the diskimage, and then just dragging <span class='file'>Atom.app</span> to the <span class='finder'>/Applications</span> folder.

Atom can be used for many writing and editing tasks, of which generating markdown text is only one. To set up Atom for creating markdown files, you need to install the necessary packages. For this blogpost I used three packages:
- markdown-writer,
- markdown-preview-plus, and
- markdown-toc.

To install these packages, start <span class='app'>Atom</span>. Then go via the Atom menu:

<span class='menu'>Atom : Preferences</span>

The <span class='tab'>Settings</span> pane opens in the main window. In the navigation part of the pane, click <span class='button'>Packages</span> to see which packages are installed. To install other packages (and Themes) click on the <span class='button'>Install</span> button at the bottom of the navigation part of the <span class='tab'>Settings</span> pane. In the box for <span class='textbox'>Search packages</span> that appears, write the name or content of the package you want to install, and hit return. You will get a list of packages that fit your search. Click on the <span class='button'>Install</span> button for the package you want to install.

You do not need to use Atom right now, but if you want to try it out for writing markdown code, go via the Atom main menu:

<span class='menu'>Packages : Markdown Writer : File : Add New Post</span>

To actually write the blog, you need to learn how markdown interprets different codes written into the pure text. For instance how to set different headings, typefaces, and bold, italics or underscore. The approach used by Atom is similar to TeXShop (even if the coding varies), and this is a main reason that I chose to use Jekyll and Atom for writing this blog post.

We are not going to use Atom until we have created a template blog using Jekyll, so let us proceed and install Jekyll and its dependencies.

## Install Jekyll dependencies

Jekyll is written in the programming language [Ruby](https://www.ruby-lang.org/), and even if macOS contains a system version of Ruby, I recommend installing a stand alone version of Ruby to use with non-system applications (apps). Doing so, however, turns into a cascade of dependencies being required, and you need to sequentially install:

* [Xcode](https://developer.apple.com/xcode/)
* [Xcode Command Line Tool tools](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=891bd3417a7776362562d2197f89480a8547b108fd934911bcbea0110d07f757&path=%2Fdownload%2Fmore%2F&rv=1)
* [Homebrew](https://brew.sh)
* [Ruby Version Manager (RVM)](https://rvm.io)
* [Ruby](https://www.ruby-lang.org/en/)

Xcode is installed via the Apple <span class='app'>App store.app </span>(an app installed with macOS), Xcode Command Line Tool by dowloading a disk image (.dmg) that contains a package installer (.pkg). Homebrew, RVM and Ruby are installed by commands written in the Terminal. If you are not used to the Terminal, the next section includes a short introduction.

### Opening and understanding the Terminal

The Terminal provides text-based access to the operating system, in macOS as well in other operating systems.

The Terminal itself is an app, and on macOS you find it under:

<span class='finder'>/Applications/Utilities</span>

You will use the Terminal quite a lot if you follow this blog, so it is handy to drag it onto your dock. Open a terminal session by double clicking the <span class='app'>Terminal</span> icon. You should see a window with a cursor and prompt, including the following components:

<span class = 'terminal'>computername:~ myuser$</span>

where 'computername' is the name of the computer, the tilde (~) indicates that you are in your home directory, 'myuser' the name of the current user, and a trailing $ which is the prompt for input.

### Install Xcode and its Command Line Tool

**Note**, with later versions of Brew (Homebrew), the necessary Command Line Tool is automatically installed when you install Brew. Thus you can safely skip this step, unless you also intend to use Xcode.

Before installing Jekyll on a mac, the Apple developer environment Xcode, and its [Command Line Tool](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=891bd3417a7776362562d2197f89480a8547b108fd934911bcbea0110d07f757&path=%2Fdownload%2Fmore%2F&rv=1), must be installed.

Xcode is an app, and if you have it installed, it will be in your <span class ='finder'>/Applications</span> folder. If not, Xcode is available from the Apple <span class='app'>App store</span>, that is installed with all recent macOS:

<span class='finder'>/Applications/App store.app</span>

You also need the Xcode Command Line Tool, that includes a compiler for Open Source projects called GCC. To check if you have GCC installed, open a <span class='app'>Terminal</span> window and type at the prompt:

<span class = 'terminal'>$ gcc --version</span>

If a version is returned, you are probably fine to go. Otherwise, you must download and install the [Command Line Tools](https://developer.apple.com/xcode/features/) for Xcode. To access the downloads you may need to register as an Apple developer. Once you are on the downloads page, search the appropriate version of your macOS. Click on the .dmg link to download it. Once it has finished downloading, simply double-click the .dmg file and then double-click the enclosed .pkg file to start the installation process.

### Install Homebrew

[Homebrew](https://brew.sh) (or Brew for short) in a package (or app) manager, that installs apps on macOS platforms. There are alternatives to Homebrew (including Fink and MacPorts). I have tried them all, and I like Homebrew better than the other two.

To install Homebrew, open a <span class='app'>Terminal</span> window and type (or copy and paste) the command:

<span class = 'terminal'>$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"</span>

Homebrew will create a special repository of installed packages and then symlinks their files into <span class='file'>/usr/local</span>.

Note that Homebrew uses the macOS version of Ruby, but it is better to have a separate Ruby installation for handling non system Apps, including Jekyll. The next step is thus to install the Ruby Version Manager (RVM) and then the latest version of Ruby as a separate stand alone app.

### Install Ruby Version Manger (RVM)

The [Ruby Version Manager (RVM)](https://rvm.io) is used for managing stand alone versions of Ruby, and also allows you to access that Ruby version directly from the Terminal prompt. To install RVM, open a <span class='app'>Terminal</span> window, and write:

<span class = 'terminal'>$ curl -L https://get.rvm.io | bash -s stable</span>

This installs RVM for your user. Note the last lines at the Terminal prompt when the installation is completed, as you might need to edit your system profile file. If you are requested to edit your system profile file (either <span class = 'file'>.bash_profile</span> or <span class = 'file'>.profile</span>), you need a text editor to open and edit files from the Terminal window. Terminal comes with some different text editors, and I use pico for editing system files. To be able to edit system files you need to tell the system that you have the rights to do so, and that you do with the command sudo (interpreted as superuser do or substitute user do). In combination you should thus write the following command at the Terminal prompt:

<span class = 'terminal'>$ sudo pico .bash_profile</span>

or

<span class = 'terminal'>$ sudo pico .profile</span>

You must give your user password to access and edit the indicated file (<span class = 'file'>.bash_profile</span> or <span class = 'file'>.profile</span>). Add the text that the RVM installation suggested. Save the edited profile file by pressing the keys for ctrl and X simultaneously (ctrl-x), hit the Y key when asked to save the file, and you have edited the system profile. You need to close and reopen the Terminal window for the changes to take effect.

To start using RVM you need to execute another Terminal command,

<span class = 'terminal'>$ source .rvm/scripts/rvm</span>

in all your open Terminal windows. Then close all open Terminal windows, and reopen a new Terminal window.

Confirm that RVM is being properly loaded in the new Terminal session by typing

<span class = 'terminal'>$ rvm version</span>

Older versions required a hyphen in from of version (<span class = 'terminal'>$ rvm --version</span>), but with later versions you have to omit the hyphen.

You should see a version number with no errors.

### Install Ruby

With RVM installed, install the latest Ruby version (2.6.3 at time of writing the update in August 2019) from the Terminal:

<span class = 'terminal'>$ rvm install 2.6.3</span>

The RVM installation will first search for a predefined (binary) installer, and if not proceed to compile the requested version from source. In the latter case RVM relies on Homebrew. If Homebrew is not installed, RVM will automatically install Homebrew after asking for permission.

When the installation is done, close your Terminal session and open a new Terminal session. Set the version of Ruby that you installed to the current version by typing:

<span class = 'terminal'>$ rvm default use 2.6.3</span>

or (<span class = 'terminal'>$ rvm -default use 2.6.3</span>)

This also sets the default version to be used whenever you open any new Terminal session.

Verify that the current Ruby version by typing

<span class = 'terminal'>$ ruby -v</span>

(Ruby itself still requires the hyphen, it is only RVM taht can do without.)

Generate the core Ruby documentation by typing

<span class = 'terminal'>$ rvm docs generate-ri</span>

You are done installing a stand alone Ruby version that is now the default Ruby version accessed by the Terminal.

Note that if you want to use the [Rails programming language](http://rubyonrails.org) with Ruby, you must install that on top of Ruby.

## Install Jekyll

Open a new Terminal window. Make sure that your Terminal links to the Ruby version you installed above, by typing:

<span class = 'terminal'>$ ruby -v</span>

The Terminal window should return the version you installed above.

To install Jekyll enter the following command at the Terminal prompt:

<span class = 'terminal'>$ gem install jekyll bundler</span>

If your system requires root permissions to install Jekyll, you have to add sudo, and instead write:

<span class = 'terminal'>$ sudo gem install jekyll bundler</span>

You will then be prompted to give the root user password, whereafter the installation will proceed.

If you followed the instructions above, and installed a stand alone version of Ruby using RVM, and told the system to use this version as the default Ruby version from the Terminal, you will have access to Jekyll whenever you get back to the Terminal. If you used the macOS Ruby version, you will not.

When the Jekyll installation is complete, you can create a blog by writing the following command at the Terminal prompt:

<span class = 'terminal'>$ jekyll new setup-blog</span> (instead of setup-blog you can write any name)

Change directory (cd) to the newly created blog by writing at the prompt:

<span class = 'terminal'>$ cd setup-blog</span>

Press the return button, and the terminal prompt should indicate that you are in the folder called setup-blog.

Jekyll comes with a default blog that explains how it works. The blog is, however, not available until you tell Jekyll to create it:

<span class = 'terminal'>$ bundle exec jekyll serve</span>

With this command, Jekyll takes the setup files (that will be edited below) and the markdown files it can find, and generates the entire blog, including all blogposts. At the same time Jekyll creates a local server on your computer allowing you to browse the blog. The local url of your blog is written at the prompt (default is http://127.0.0.1:4000/). Copy the url and paste it into your web-browser.

In the browser you can see the blog front page, and the Jekyll example blog. They contain useful information on how to edit the included files to suite your blog.

Jekyll will live update the local server when you make changes in your Atom Project. You only need to refresh the local web page in your browser to see any changes. So leave the server running. Otherwise you close the server from the Terminal prompt by pressing the keys ctrl and C at the same time:

<span class = 'terminal'>$ ctrl-c</span>

### Edit the configuration (\_config.yml)

The Jekyll example blog is of course not want you want to publish. The main controller of the common content and layout of all the pages in your blog is in the file <span class = 'file'>\_config.yml. \_config.yml</span> is a static file, and the content of <span class = 'file'>\_config.yml</span> will be reflected in all pages related to your blog.

Start <span class='app'>Atom</span>, and wait for the <span class = 'tab'>Welcome Guide</span> pane to open. In the <span class = 'tab'>Welcome Guide</span> click <span class = 'button'>Open Project</span>, then navigate to the folder you created with Jekyll (<span class = 'file'>setup-blog</span>), and select the folder itself as the Project. A <span class = 'tab'>Project</span> pane will open in the Atom window. In the <span class = 'tab'>Project</span> pane, click the <span class = 'file'>\_config.yml</span> file.

<span class = 'file'>\_config.yml</span> file is well commented, and you can enter the details for the blog you are about to create. Change the title, description and baseurl tags, where the latter should have the same name as your Project (which will become an online repository if you later share it in GitHub as described in the [next blog](https://karttur.github.io/setup-github/index.html)). Here is an excerpt of <span class = 'file'>\_config.yml</span> for this blog post:

```
title: Geo Imagine Developer
description: >- # this means to ignore newlines until "baseurl:"
  Remote sensing and spatial data developer guide
  for global natural resources mapping,
  inventories and monitoring.
baseurl: "/setup-blog" # the subpath of your site
markdown: kramdown
theme: minima
```

Then I also edited the file <span class = 'file'>\_about.md</span>:
```
---
layout: page
title: About
permalink: /about/
---

The Geo Imagine Developer blog is maintained by Thomas Gumbricht (Karttur AB) [karttur.com](https://karttur.com/)
```

### Cusomized CSS

There are different options for changing the Cascading Style Sheet (CSS) that defines your blog layout and style. The CSS file that defines the overall style of html pages is in the <head> tag of the html file. By default the Jekyll [minima theme](https://github.com/jekyll/minima) (used in here), links to the CSS file <span class='file'>/assets/main.css</span>. This CSS file is generated by Jekyll, but we can bypass the default CSS file, by:

1. Extending the default CSS
2. Create Customised \_includes
3. Linking the extended CSS to the customised \_includes

#### Extending the CSS

In the Atom <span class='tab'>Project</span> pane, locate the folder <span class='file'>\_site</span>. The folder contains your static web page generated by Jekyll. In the subfolder <span class='file'>\_site/assets</span> you will see the file <span class='file'>main.css</span>, the default CSS file in the theme minima. Just leave it.

Create a file called <span class='file'>/assets/css/style.scss</span> in your Project (repository). To create the path <span class='file'>/assets/css</span> and the file <span class='file'>style.scss</span> you can use Atom. Select the Project root folder (setup-blog) and ctrl-click (or left click) on your track pad or mouse, from the list that appears you can choose to create both folders and files.

Add the following content to the beginning of the file <span class='file'>style.scss</span>:
{% raw %}
```
---
---

@import "{{ site.theme }}";
```
{% endraw %}
Custom CSS added after the @import line will be added to the default css file, and the combined css file saved in your <span class='file'>\_site</span> folder with the path cloned from your customised css file (this will clear further down).

For this blog I added the css styles used for highlighting different object types (<span class='menu'>menu</span>, <span class='button'>buttons</span>,<span class='tab'>tabs and panes</span> etc). As an example, the style for <span class='menu'>menu</span> is:
```
.menu {
       background-color: #DCDCDC;
       color: black;
       font-family: "Times New Roman", Times, serif;
       font-size:large;
       border: 1px solid black;
   }
```
If your Jekyll server is up and running, a new subfolder with a css file will appear <span class='file'>\_site/assets/css/styles.css</span>. If you open that css file in Atom, and compare it with <span class='file'>\_site/assets/main.css</span>, you will see that the two are identical, except that <span class='file'>\_site/assets/css/styles.css</span> is extended with the code you entered in <span class='file'>/assets/css/style.scss</span>.

#### Customised \_includes

You now have to change your blog html files to point to the extended CSS file. This is done by creating a new file <span class='file'>\_includes/head.html</span>. This file will take precedence over the default minima theme head.html. Go ahead and create the file <span class='file'>\_includes/head.html</span>, and copy and paste the following code:
{% raw %}
```
<head>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  {% seo %}
  <link rel="stylesheet" href="{{ "/assets/css/styles.css" | relative_url }}">
  <link rel="alternate" type="application/rss+xml" title="{{ site.title | escape }}" href="{{ "/feed.xml" | relative_url }}">
  {% if jekyll.environment == 'production' and site.google_analytics %}
    {% include google-analytics.html %}
  {% endif %}
</head>
```
{% endraw %}
The only difference compared to the minima theme head.html is the link to the stylesheet.

If this was a perfect world, the Jekyll server should now serve up your restyled web page. But my version of Jekyll (3.6.2) did not. Instead it reports an error (in the Terminal window). The errors is caused by the seo tag in the local version of <span class='file'>head.html</span>, the file that you just created.
{% raw %}
```
{% seo %}
```
{% endraw %}

The seo tag creates data for search engines, and requires both a special gem, and to be included in the <span class='file'>\_config.yml</span> file. Let us fix that.

In Atom, open the <span class='file'>Gemfile</span> in top directory of your Project, and add the gem for the seo tag, by adding the following line:
```
gem "jekyll-seo-tag"
```
Save the <span class='file'>Gemfile</span>.

Open <span class='file'>\_config.yml</span> and add the seo tag as a plugin:
```
plugins:
  - jekyll-seo-tag
```
If you are using a Jekyll version less than 3.5.0, use the 'gems' key instead of 'plugins'.

Remember to save <span class='file'>\_config.yml</span> after editing.

Your restyled web page should be served up.

### Writing this blog post

The text and style of this blog is written using Markdown Writer in Atom. The theme is set in the file <span class = 'file'>\_config.yml</span>, using a single command:
```
theme: minima
```
When writing the blog I only used a few markdown codes.
```
Headings (there must be a space after the #)
# H1
## H2
### H3
```
```
Bold typeface
**bold text**
```
```
Unordered list
- (or +, or *)
```
```
Url link
[text](url)
```
I finally used the package markdown-toc to generate the table of contents.

The first paragraphs of text in the markdown file used for generating this blog post illustrates how the markdown coding works:
```
---
layout: post
title: "Set up blog tools: Jekyll and Atom"
date: "2017-12-21 07:58"
---
**Contents**
	- [Introduction](#introduction)
	- [Install Atom](#install-atom)
...

...
## Introduction

This blog post is for remembering how I set up the tools for writing my own blog posts.

After looking at different alternatives, I decided to try [Jekyll](https://jekyllrb.com) that is available from [GitHub](https://github.com).
```
The code snippet between the triple hyphens (---) at the beginning is the YAML front matter. For this blog post it only defines the document layout and title, but it can include several other definitions.

## Next blog - Setup GitHub pages

This blog post is set up using the Jekyll default theme (minima).  My [next blog](https://karttur.github.io/setup-github/index.html), is created without any template, and includes how to publish the blog on [GitHub.com](https://github.com).

## Resources

[Atom](https://atom.io)

[Atom mardown editing](https://discountry.github.io/2017/02/15/use-atom-as-your-markdown-editor/)

[Install Ruby](https://pragmaticstudio.com/blog/2010/9/23/install-rails-ruby-mac)

[Jekyll](https://jekyllrb.com/docs/home/)

[Jekyll mimina theme](https://github.com/jekyll/minima)

[Customizing CSS](https://help.github.com/articles/customizing-css-and-html-in-your-jekyll-theme/)

[Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

[Web safe CSS fonts](https://www.cssfontstack.com)

[Setup GitHub pages](https://karttur.github.io/setup-github/index.html) my next blog
