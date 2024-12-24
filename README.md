# Introduction. 
This repository contains the raw content for my personal website, generated using Hugo.

You can visit the published website through here: [donalglavin.github.io](https://donalglavin.github.io)
*Thanks to GitHub actions its compiled and published upon every update.*

The purpose of this website is for sharing information, knowledge and ideas whilst also making 
a little money on the side to fund future projects and posts. 

As such, I've created the following post to help others learn and develop their skills 
in static site generation with Hugo and GitHub actions.

# Overview. 
This guide will walk you through the steps of creating your own Hugo site, 
linking it to a GitHub repository, applying a theme, and deploying it to GitHub 
Pages for free hosting.

The end result, should be a professional looking website for you to call your own.

The requirements for you to achieve this are:
- A GitHub account. (free to sign up for personal use). 
- A Computer with the ability for you to install software.
- Git (an application, different from GitHub).
- Hugo (The tool used to build static sites). 
- *(optional)* a Markdown editor of your choosing (VSCode is a reasonable entry point and is free).

## Installing Resources.
- If you're on windows I'd recommend using the [scoop.sh](https://scoop.sh) application
to install both git and Hugo (as well as a markdown editor). 
Have a look on line on how to install applications (it's a fantastic tool). 
- If you're on Mac you can use [homebrew](https://brew.sh) for a similar experience. 
- If you're using Linux (I trust you probably didn't read this).

# Methodology.
## Step 1. - Creating the repository and configuring GitHub actions.
The following section outlines how to generate the site and the corresponding 

### Step 1.0 - Hugo New Site.
Create a new Hugo site using the following command:
*I use Yaml as it is easier to read than Toml*

```shell
hugo new site 'your-site-name' --format yaml
```

This will create a directory named 'your-site-name' with the following sub-directories:

 -   archetypes
 -   assets
 -   content
 -   data
 -   i18n
 -   layouts
 -   public
 -   static
 -   themes
 - 󰉢  hugo.yaml

### Step 1.1 - Creating the repository.
1. Go to your GitHub account and click "New" to create a new repository.
1. Name the repository (it can be the same as 'your-site-name').
1. Choose between "Public" or "Private" visibility.

### Step 1.2 - Linking the Hugo new site to your Git repo.
Initialize a Git repository in your Hugo site directory:
```shell
cd 'your-site-name'
git init
```

(Optional but recommended) Create a .gitignore file to exclude unnecessary files from your repository:
*The following site can be used to create generic .gitignore templates [toptal.com](https://www.toptal.com/developers/gitignore)*

Add and commit the initial files:
```shell
git add .
git commit -m "initial commit"
```

Set the main branch as the default:
```shell
git branch -M main
```

Add the remote repository:
```shell
git remote add origin https://github.com/'your-github-username'/'your-repository-name'.git
```

Push the code to the repository:
```shell
git push -u origin main
```

## Step 2. - Adding a Theme.
1. Browse the Hugo Themes website: [themes.gohugo.io](https://themes.gohugo.io/)
2. Choose a theme and copy its GitHub URL.
3. Add the theme as a Git submodule:

```shell 
git submodule add 'theme-github-url' themes/'theme-name'
```

Initialize and update the submodule
```shell
git submodule update --init --recursive
```

Follow the theme's documentation to configure it. Some themes may have an exampleSite directory that you can use as a starting point.

## Step 3. - Adding the upload destination. 
1. If you don't have one, create a special repository named 'your-github-username'.github.io.
2. Go to the repository settings and enable GitHub Pages. Your website URL will be: https://'your-github-username'.github.io
3. In your Hugo site directory, delete the public folder if it exists.
4. Add your GitHub Pages repository as a submodule in the public directory:

Next all you need to do is to delete the public folder in your blog and run the command below: 
```shell
git submodule add https://github.com/'your-username'/'your-username'.github.io.git public
```
Build your site with the chosen theme:
```shell 
hugo -t 'theme'
```
Commit and push the generated site to GitHub:
```shell
git add . 
git commit -m "Initial Website Upload"
git push
```
And that's it. 
