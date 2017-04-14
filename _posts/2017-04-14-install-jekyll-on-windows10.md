---
layout: post
title: "install jekyll on windows"
description: "Use jekyll in local windows machine"
headline: =============================================
category: Setup
tags: [jekyll, windows]
imagefeature: default_bg.jpg
comments: true
mathjax: false
---

[offical site](https://jekyllrb.com/docs/windows/)
# Install a package manager for Windows called Chocolatey
open cmd(within admin), and run

```
@powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"

```

# Install Ruby via Chocolatey
 `choco install ruby -y`
# **Reopen** a command prompt and install Jekyll
 `gem install jekyll`

###  **my error**:

 ```
 Unable to download data from https://rubygems.org/ - SSL_connect returned=1 errno=0 state=SSLv3 read server certificate
 B: certificate verify failed (https://api.rubygems.org/specs.4.8.gz)
 ```

### [**solution**]
(http://stackoverflow.com/questions/19150017/ssl-error-when-installing-rubygems-unable-to-pull-data-from-https-rubygems-o/27298259#27298259)
 Goto link http://rubygems.org/pages/download
 - Download the latest zip file (In my case 2.4.5)
 - Unzip it
 - run "ruby setup.rb" in unzipped folder
 - now run gem install command


# you may need bundle

`gem install bundler`

# install gem packages
`bundle install`

### error:

```
Dependency Error: Yikes! It looks like you don't have tzinfo or one of its dependencies installed. In order to use Jekyll as currently configured, you'll need to install this gem. The full error message from Ruby
 is: 'cannot load such file -- tzinfo' If you run into trouble, you can find helpful resources at https://jekyllrb.com/help/!
jekyll 3.4.3 | Error:  tzinfo

```

### solution: [reference](https://github.com/jekyll/jekyll/issues/5935)
`gem install tzinfo`
`gem install tzinfo-data`
add `gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw, :jruby]` to your Gemfile
and rerun `bundle install`

# end
`bundle exec jekyll serve`


