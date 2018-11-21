# Jekyll on Ubuntu Xenial (v16.04 LTS)

**WARNING** The first time starting this vagrant image takes about 7 minutes.


## Jekyll - Quick-start guide

Start creating Jekyll pages, with this vagrant VM images.

Launch the vagrant box

    $ vagrant box update

    $ vagrant up

    $ vagrant ssh

There is this Jekyll [Quick-start guide](https://jekyllrb.com/docs/quickstart/).
The first step is not needed, as Jekyll is already installed during `vagrant up`.

Start with the second command onward

    # Create a new Jekyll site at ./myblog
    ~ $ jekyll new myblog

Launch Jekyll with the follow command

    # Build the site on the preview server
    ~/myblog $ bundle exec jekyll serve --host 192.168.33.10

On the host computer open in a browser http://192.168.33.10:4000/


## Edit an already existing Jekyll GitHub pages project

Open the `Vagrantfile` and uncomment the line `config.vm.synced_folder` update the first
value `~/git/project-name`, which is the directory on the host.

Launch the vagrant box

    $ vagrant box update

    $ vagrant up

    $ vagrant ssh

Show which Gem packages have been installed

    $ gem list

Enter the jekyll project

    $ cd jekyll-site

Check if there is a `Gemfile`, if not follow the instructions [Setting up your GitHub Pages site locally with Jekyll](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/)

Create the `Gemfile`

    source "https://rubygems.org"

    # Hello! This is where you manage which Jekyll version is used to run.
    # When you want to use a different version, change it below, save the
    # file and run `bundle install`. Run Jekyll with `bundle exec`, like so:
    #
    #     bundle exec jekyll serve
    #
    # This will help ensure the proper Jekyll version is running.
    # Happy Jekylling!
    #gem "jekyll", "3.5.1"

    # This is the default theme for new Jekyll sites. You may change this to anything you like.
    gem "minima", "~> 2.0"

    # If you want to use GitHub Pages, remove the "gem "jekyll"" above and
    # uncomment the line below. To upgrade, run `bundle update github-pages`.
    gem "github-pages", group: :jekyll_plugins

    # If you have any plugins, put them here!
    group :jekyll_plugins do
       gem "jekyll-feed", "~> 0.6"
    end

    # Windows does not include zoneinfo files, so bundle the tzinfo-data gem
    gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw, :jruby]

Install Jekyll and other dependencies

    $ bundle install

Keeping your site up to date with the GitHub Pages gem

    $ bundle update

Launch jekyll pages

    ~/jekyll-site $ bundle exec jekyll serve --host 192.168.33.10

On the host computer open in a browser http://192.168.33.10:4000/
