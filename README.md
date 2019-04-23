# al-folio

[![build status](https://travis-ci.org/alshedivat/al-folio.svg?branch=master)](https://travis-ci.org/alshedivat/al-folio)
[![demo](https://img.shields.io/badge/theme-demo-brightgreen.svg)](https://alshedivat.github.io/al-folio/)
[![license](https://img.shields.io/github/license/mashape/apistatus.svg?maxAge=2592000)](https://github.com/alshedivat/al-folio/blob/master/LICENSE)
[![gitter](https://badges.gitter.im/alshedivat/al-folio.svg)](https://gitter.im/alshedivat/al-folio?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

A simple and clean [Jekyll](https://jekyllrb.com/) theme for academics.

[![Screenshot](assets/img/full-screenshot.png)](https://alshedivat.github.io/al-folio/)

Originally, **al-folio** was based on the [\*folio theme](https://github.com/bogoli/-folio) (published by [Lia Bogoev](http://liabogoev.com) and under the MIT license).
Since then, it got a full re-write of the styles and many additional cool features.
The emphasis is on whitespace, transparency, and academic usage: [theme demo](https://alshedivat.github.io/al-folio/).

## Getting started

**I follow the instructions shown on [the orginal site](https://github.com/alshedivat/al-folio) and add some more steps to follow here.**

### Installation

1. Install [Jekyll](https://jekyllrb.com/docs/installation/macos/)
We're going to install Jekyll locally before deploying anything to GitHub pages.
Install Command Line Tools
Open Terminal. Check to see if you have XCode Command Line Tools installed by typing gcc -v. At this point, it will prompt you to install if you don't. Or run this code to install:
```bash
$ xcode-select --install
```

2. Install [Ruby](https://www.ruby-lang.org/en/downloads/) 
Ruby should come pre-installed on all OSX computers. You can check if Ruby is installed by running ruby -v. It should return with Ruby version 2.0.0 or higher.
ruby 2.0.0p645 (2015-04-13 revision 50299) [universal.x86_64-darwin15]
If for some reason you're running a lower version, you can update.
```bash
$ sudo gem install ruby
```

3. Install [Bundler](https://bundler.io/)
Bundler is a package manager that will aid you in installing all the Jekyll dependencies.
```bash
$ sudo gem install bundler
```

4. Fork the theme from `github.com:alshedivat/al-folio` to `github.com:<your-username>/<your-repo-name>` (get an instruction [here](https://help.github.com/en/articles/fork-a-repo) and do the following:

```bash
$ git clone git@github.com:<your-username>/<your-repo-name>.git
$ cd <your-repo-name>
$ bundle install
$ bundle exec jekyll serve
```

For example, you can type:
```bash
$ git clone git@github.com:yongwanlim/yongwanlim.github.io.git
$ cd yongwanlim.github.io
$ bundle install
$ bundle exec jekyll serve
```

5. Now, feel free to customize the theme however you like (don't forget to change the name!). After you are done, **commit** your final changes.
```bash
$ git remote -v
$ git status
$ git add .
$ git commit -m “initial commit”

6. Modify your `_config.yml`
**Note:** when deploying your user or organization page, make sure the `_config.yml` has `url` and `baseurl` fields as follows.

```
url: # should be empty
baseurl:  # should be empty
```

7. Deploy your website to [GitHub Pages](https://pages.github.com/) by running the deploy script:

```bash
$ ./bin/deploy --user
```

**al-folio** said: 

> By default, the script uses the `master` branch for the source code and deploys the webpage to `gh-pages`.
The optional flag `--user` tells it to deploy to `master` and use `source` for the source code instead.
Using `master` for deployment is a convention for [user and organization pages](https://help.github.com/articles/user-organization-and-project-pages/).

8. Now, you are set. Visit <your-username>/<your-repo-name>. Here, my webpage address for example, yongwanlim.github.io. 

### For more information

I found here useful informations:

https://github.com/alshedivat/al-folio
https://www.taniarascia.com/make-a-static-website-with-jekyll/
https://jekyllrb.com/docs/installation/macos/


## License

The theme is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).
