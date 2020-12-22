# Overview

This site is my personal experience using: [<img src="https://github.com/jcaughlin/jcaughlin.github.io/blob/master/static/images/hugo-logo-wide.svg" alt="Hugo" width=200>](https://gohugo.io)

<p>Hugo has nice things to say about Hugo:</p>

> The world’s fastest framework for building websites

> Hugo is one of the most popular open-source static site generators. With its amazing speed and flexibility, Hugo makes building websites fun again.

<p>Hugo is dependent on having Go installed order to work , but I haven't gotten to a point where I actually needed to know Go.

## How I Built This:
- Built on: MacBook Air (13-inch, Early 2014) MacOS BigSur
### Step 0: Homebrew
As I wanted Hugo to be in my PATH, but I didn't really want to think, I installed Hugo using Homebrew [brew.sh]( https://brew.sh) I'm assuming anyone following my path will either already have Homebrew installed or will go to Homebrew's site to do this. Homebrew as a package manager is its own topic. You can't install Homebrew with Homebrew because if you have Homebrew you don't need to install it and if you don't have Homebrew you can't install anything.

Why I use Homebrew for some packages and not others is not something I always analyse. If you really want a better opinion, Hugo has a list of [Pro's and Con's](https://gohugo.io/getting-started/installing/) that is much more eloquent than anything I could come up with. In fact, quit reading this and go read their instructions! Just Kidding. As I deployed my site using Github Pages, there are a couple highlights that I point out that streamlined my workflow.

### Step 1: Prerequisites
<P>You can install the following two packages using Homebrew, but I think they are important enough that you should visit their websites and be somewhat familar with where to find documentation.</p>
-  [git](https://git-scm.com) installed
-  Install [Go](http://golang.org)

### Step 2: Install Hugo
Assuming Homebrew is installed:
```
brew install hugo
```
To confirm that hugo is installed:
```
hugo version
```
Please note that it is just version with no '-'. It isn't `hugo -v` either. The first earns you an error message and the latter will try to build a site verbosely. I suppose if either of these things happen you know hugo is installed and doing something, but if you actually want to know what version you are using stick with `hugo version`.

Can I just stop assuming? Anyways, if you aren't familiar with homebrew and where the magic happens, don't forget the handy which command:
```
which hugo
```
Typically, this is the result you will get:
```
/usr/local/bin/hugo
```

### Step 3: Create a New Site
```
hugo new site your-clever-site-name-goes-here
```

### Step 4: git er done with git and github
When hugo creates your project/directory structure, it isn't initialized as a git repository. I know this is common in other languages and frameworks, but if you want to do anything with github and/or version control, this is the step where you:
```
git init
```
There are much better places to get an opinion on a good .gitignore file would be for a hugo project. If you want, copy mine. If you think you can do better, let me know. I am not an expert at this.

**Question:** How many times have you tried to add a remote repository and got an error message because you initialized your project, but forgot to do an initial commit? I swear every other time I do this.

### Step 5: Add a Theme

