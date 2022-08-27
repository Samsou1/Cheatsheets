# Gemfile

First you need to create the Gemfile
```shell
touch Gemfile
```

Then put all the gems you will need. For instance:
```shell
source "https://rubygems.org"
ruby '2.7.4'
gem 'rspec'
gem 'pry'
gem 'rubocop'
gem 'nokogiri'
```

And finally in the command that creates  Gemfile.lock
```shell
bundle install
```