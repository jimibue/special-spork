# README
This is an example of how to initiate a Billboard with artists and songs

## Must have installed
* Ruby
* Rails
* VSC 

# Gems
* gem 'better_errors'
* gem 'binding_of_caller'
* gem 'pry-rails'
* gem "faker", :git => "https://github.com/faker-ruby/faker.git", :branch => "master"
* gem 'semantic-ui-sass'
* "**BUNDLE INSTALL**"

# Getting started
* Create your app in rails using desired database (postgres, etc)
* Create your models for Billboard, artists, and songs in rails
* Set up the model associations as has_many :through associations
* In app/models/artists.rb "has_many :songs, has_many :billboards through: :songs"
* In app/models/billboards.rb "has_many :songs, has_many artists, through: :songs
* Generate your controllers for your models
* Fill out all your CRUD actions
* Fill out index, show, new, html.pages
* Add finishing touches nav bar, color, and links 
* Marvel at the glorious app you have created :grinning:
