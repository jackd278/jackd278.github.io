---
title: Creating This Website
date: 2024-08-10 17:00:00 -400
categories: [website]
Tags: [website, resume, personal, ruby, github, cd\ci. devops]
---

# How I created this Site

I started by following these instructions from TechnoTim: [TecnhoTim Jekyll Doc site](https://technotim.live/posts/jekyll-docs-site/)

Then I cloned the repo in my github account: [My Website Github Clone](https://github.com/JD8278/jackwebsite)

Here is a link to the Chirpy Theme documentation: [Chirpy Documentation](https://chirpy.cotes.page/posts/text-and-typography/)

When attempting to bundle my site I had to do several updates to my ubuntu windows subsystem for linux.


```bash
sudo apt update
sudo apt upgrade
sudo apt install ruby-full build-essential zlib1g-dev git
```
To avoid installing RubyGems packages as the root user:

If you are using bash (usually the default for most)
```bash
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```
I needed to install Ruby Version Manager in order to get the right version for all the dependencies. I used this site to get the commands: [Ruby Version Manager](https://rvm.io/rvm/install)

Then I needed to know which version I actually wanted, so here is a list of released ruby versions: [Ruby Versions](https://www.ruby-lang.org/en/downloads/releases/)

I ended up using Ruby 3.2.5 based on the error messages I received when trying to install and bundle this site.

Install Jekyll bundler
```bash
gem install jekyll bundler
```
After creating a site based on the template, clone your repo
```bash
git clone git@<YOUR-USER-NAME>/<YOUR-REPO-NAME>.git
```

After this you can start creating posts in the post folder using markdown. Here is a guide on Markdown I found: [Markdown Guide](https://www.markdownguide.org/basic-syntax/)
