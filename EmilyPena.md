Submitted by: Emily P

# Class and Instance Method
---
## Class Method
* A class method is a method that is called on the class itself, not on the instances of that class
* Self. refers to the whole class not the instance
* Use Class Methods when the functionality you are writing does not belong to an instance of that class

#### Example:
```ruby
class Basket  
def self.find(id)  
puts "finding basket with the id of #{id}"  
end  
end  
```

## Instance Method
* Provides functionality to one instance of a class
* We cannot call an instance method on the class itself
* Getter and setter methods/attr_accessor

#### Example:
```ruby
class Foo
  def baz
    puts 'instance method'
  end
end
```
or
```ruby
class Foo
  attr_accessor :baz
end
```

# Class and Instance Variables
---
## Class Variables
* @@
* A class variable is accessible to the entire class - class scope
* Shared by all objects of a class

#### Example:
```ruby
class Album
  @@album_count = 0

  def self.count
    @@album_count
  end
end
```

## Instance Variables
* Responsible for holding information regarding a instance of a class and is only accessible to the instance of the class
* @

#### Example:
```ruby
class Person
  def initialize(name)
    @name = name
  end
end
```




# Rails Routes
---
* The rails router is a the place that holds the URLs and directs them to the controller action.
* The routes for the application linve in the config/routes.rb file.

## Resource Routing
* Resource routing is a default and quick way to declare common routes for a controller.

#### Example:
```ruby
resources :routes
```

* Resource routing can also be defined with multiple resources at the same time.

#### Example:
```ruby
resources :photos, :books, :videos
```

## Nested Resources
* Nested Resources allows you to route the nested relationship to your controller.

#### Example:
```ruby
resources :magazines do
  resources :ads
end
```

* To many nested resources can become problematic so keeping it to two is good convention.

## Shallow Resources
* One way to avoid over nesting is to use shallow nesting. This allows you to generate actions under the parent, so there is still a hierarchy but not nested.

#### Example:
```ruby
resources :articles do
  resources :comments, only: [:index, :new, :create]
end
resources :comments, only: [:show, :edit, :update, :destroy]
```

## Generate paths
* It is also possible to generate paths and URLs to paths.

#### Example:
```ruby
get '/patients/:id', to: 'patients#show', as: 'patient'
```

* In this example the router will generate a path to the patient ID.