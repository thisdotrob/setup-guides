# Sinatra / Capybara / Travis CI / Coveralls / Guard
- [Base setup](#base-setup)
- [User setup](#user-setup)
- [Running tests](#running-tests)
- [Usage](#usage)

## Base setup
0. Install Ruby and Bundler
0. Create a `Gemfile` containing:
  ```ruby
  source 'https://rubygems.org'

  ruby '2.3.0'

  gem 'sinatra'

  group :test do
    gem 'coveralls', require: false
    gem 'rspec-sinatra'
    gem 'capybara'
  end

  group :development do
    gem 'guard'
    gem 'guard-rspec', require: false
  end
  ```
0. Run `bundle install`
0. Run `rspec-sinatra init --app AppNane app.rb`
0. Add `.rspec` containing:
  ```
  --require spec_helper
  --color
  --format documentation
  ```
0. Add `.travis.yml` containing:
  ```yml
  language: ruby
  rvm:
    - "2.3.0"
  script: bundle exec rspec spec
  ```
0. Add to the top of `spec_helper.rb`:
  ```ruby
  require 'coveralls'
  Coveralls.wear!
  ```
0. Run `guard init`
0. To run tests use: `rspec`
0. To continuously run, use: `bundle exec guard`

## User setup
0. Install [Ruby](ruby) and [Bundler](bundler)
0. Clone this repo: `git@github.com:thisdotrob/...`
0. Run `bundle install`

## Running tests
0. For a single test run, use `rspec`
0. For continuous testing, use `bundle exec guard`

## Usage
0. Run `ruby app.rb`
0. Visit [http://localhost:4567](http://localhost:4567)
