---
title: "Hugo and GitHub Pages-My Definitive Opinion"
date: 2020-12-21T17:01:15-06:00
---
So you want to deploy a site on GitHug Pages and you don't want to use Jekyll? Guess what? You don't have to! They can't make you do anything.
I don't think I am intending this to be a "how-to" guide, but I thought I would document some of the finer points, both for the reader's amusement, but also so that I will have a repository of my notes for when I invariably forget something I did and need to remind myself

## The Install
I have a mac and I used  [Homebrew] (https://brew.sh) to install it. I think it was as easy as 
```
brew install hugo
```
I am pretty sure you will need Go installed on your machine. I already had it, so it wasn't a factor in my installation.

## The Quickstart
Hugo's docs are pretty good, but I found the following tweaks made my life easier. By default, when you build your hugo site by calling hugo, all your public files to be published are built in a directory called "public". Every time you build something, the public directory is updated.

GitHub pages doesn't know what a public is. When you push your repository to GitHub, it(GitHub) is either looking in the root directory or for a directory called "docs". If you really want to make your life hard, You can make intialize your public directory and set the remote as the github pagee repository. In other words, in this scenario:
1) You have a directory with a github remote that stores your sources code for your github pages content.
2) WIthin this directory, you have another git repository with a remote set up to the actual github pages repository. This is the directory that under normal circumstances would be publishes.
3) Every time you rebuild your page, you would not only need to commit your source code, but you would also need to cd into your public folder and commit and push that as well.

## Make Your Life Easier and Just Change the Config 
I used toml, so I added:
```
publishDir = "docs" 
```
So know my repository is currently being built from the /docs folder in the master branch. Apparently, you can publish off of a different branch or you can choose to publish from the root of the repository. I imagine the latter scenario would be a requirementment if one were to be building a site using vanilla html/css.

I don't know. I feel like my life is better this way. I have one remote which publish to my domain. I step and no scripts and all it involved was adding a line to my config.toml and making sure that matched my settings in github.

## You can have unlimited GitHub Pages
I don't know whether this is true if you want to use custom url's, but you can set up multiple repositories to publish to their own directories. Effectively, you have a main site and everything after that is published under that domain. For instance, my main site publishes to https://jcaughlin.github.io. Any addtional github pages site, would be published as https://jcaughlin.github.io/repository-name-here. Pretty simple.

## Themes?!@!@
I still don't know everything about using themes. In my case, I would prefer to learn how to build and maintain my own themes, but in the short run, it is easiest to visit [Hugo Theme's](https://themes.gohugo.io) and pick one.

<em>DO NOT CLONE!!!</em> I don't care what the authors tell you. You don't really need or want to clones the theme's directory into your theme directory. You want to add it as a git submodule. Say you choose to use the hugh coder theme, this is your command: ```git submodule add https://github.com/luizdepra/hugo-coder.git themes/hugo-coder```
It will create a new directory in your themes directory by the name of the theme. All you have to do is add the line ```theme = "hugo-coder"` ``to your config.toml in order to start using the theme. All themes by convention contain a directory with an example site which you can find in the exampleSite directory. To start quickest, you will want to check out the config file there as it will give you some ideas on the various key-values you would want to update on your own config.toml

## You MUST git init
When you create your new site by typing ```hugo new site "your-clever-name-here```, a basic directory is generated for your site. In my correct opinion whether you intend to set this up with a remote or not, your next step should be to ```git init```. I have used a few different frameworks and build tools and more and more are defaulting to having the project being git intialized as part of the "new" command. I haven't figured out if that is something I can change to be a defaut on my end. Nor, can I reason why this was included. I just took for granted that it was there until I did a `git status` and was confused as to why I got an error message. It is not the end of the world and I am sure some people prefer not being told they must be forced to git, but that's the way it works. 

I hope this helps someone. Hopefully, I will revise it and maybe expand it to a complete "How I To" guide featuring step by step instructions. Barring that, at least I have summarized for you the reader where I found my biggest pain points and where my opinions and steps diverged from the hugo docs.

