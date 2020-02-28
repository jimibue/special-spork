# Billboard basic setup

Setting up this app is fairly straight forward.

Make sure you have Rails 6+ installed and Postgresql. 

Download all the files 
Create your database with the command line: rails db:create. Next run bundle install and get all the gems and dependences up and running.

           Startup the rails server with:
                    rails s

              login to localhost:3000

 Create a new user. Login and head back over to your command line. Run the command: rails db:seed to give yourself some data to work with. A success should give you a successful message.
 
 Have fun playing around with the fake top 100 billboard app!
 
 
 # To recreate this project
 Make sure you have rails 6+ and Postgresql installed and running
 Start the project while in the directory you want to create it,
 In your command line type: rails new billboard_plus -d posgresql
 
 everything should generate. Take a tea break. 
 
 when everything has been created add the following gems to the main section of your gemfile:
 
gem 'jquery-rails'
gem 'bootstrap', '~> 4.0.0'
gem 'devise'

then add the following gems to your development section: 

  gem 'faker', git: 'https://github.com/faker-ruby/faker.git', branch: 'master'
  gem 'meta_request'
  gem 'pry-rails'

  
  go back to your CLI and enter bundle install
  
  From here we're also going to install devise with the command: rails g devise:install
  
  After it has completed make sure you follow the on screen instructions to complete installation.
  
  # Rails code
  
  Great, now you've made it to the part where we're actually going to jump into rails.
  
  First lets create our user models:
  
  rails g devise user
  rails g model billboard name:string region:string user:belongs_to
  rails g model artist name:string genre:string user:belongs_to
  rails g model song name:string bpm:integer artist:belongs_to billboard:belongs_to
  
  rails db:create
  
  Make sure your migration files are setup how you want them to and run a good ol' rails db:migrate for good measure. 
  
  If successful you shouldn't see any error messages.
  
  # Controllers
  
  rails g controller billboards index new edit show
  rails g controller artists index new edit show
  rails g controller songs index new edit show
  
  Once our controllers are created we can start in on our user models and their parts. 
  
  ## user model
  
  In here we're going to see a few things already, leave the stuff created by devise and add:
  has_many :billboards
  has_many :artists
  has_many :songs, through: :artists
  
  # #artist model
  should show: 
  belongs_to :user
  
  add:
  has_many :songs, dependent: :destroy
  has_many :billboards, through: :songs
  
  ## billboard model
  should show: 
  belongs_to :user
  has_many :songs, dependent: :destroy
  has_many :artists, through: :songs
  
  ## song model
  belongs_to :billboard, optional: true
  belongs_to :artist
  
  ## Further setup
  
 