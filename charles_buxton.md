# Class and Instance Methods - Ruby

In Ruby, a class is an object that defines a blueprint to create other objects. Classes define which methods are available on any instance of that class.

Defining a method inside a class creates an instance method on that class. Any future instance of that class will have that method available.T

There is a difference between a class and an instance method in Ruby. Firstly, a class method can only be called on the class itself later in your code. It can't be called on a single instance of the class. Conversely, an instance method can only be called on an instance of a class and not the class itself. 

Let's look at a code example to illustrate this:
```ruby
class ClassName

 def  self.class_method
    puts "I am a class method"
 end

 def instance_method
    puts "I am an instance method"
 end
end
```
If we try to call:
`ClassName.class_method` this will return => "I am a class method"

However, if we try to call:
`ClassName.instance_method`, this yields an Unidentified Method Error

Conversely, if we try the following:
```ruby
var = ClassName.new
var.instance_method 
```
This will return "I am an instance method"

But we cannot call...
```ruby
var = ClassName.new
var.class_method
```
...as it will also return an Unidentified Method Error

So when is the right time to use one over the other? 
We want to use instance variables when there is data specific to the single instance of the class that needs methods applied to it. 
  Ex. .destory is an instance method. We want to delete a single instance and not the class itself. 

Using class methods is a better idea when we are dealing with anything that does not deal with a specific instance of that class. AKA when we want to use the methids within the class, or pass the method onto a child via inheritance. 
ActiveRecord, under the hood in Rails is a good example of this concept:
```ruby
module ActiveRecord
  class Base
    def self.validates_presence_of(...)
      # make sure present
    end
 end
end
```
The above code in ActiveRecord class gives us the ability to then call in our new model class:
```ruby
class Model < ActiveRecord::Base
  validates_presence_of :name
end
```
When you say `validates_presence_of`, the class method in AR::Base is what gets called.

The above code in ActiveRecord class gives us the ability to then call in our new model class:
`class Model < ActiveRecord::Base`
  `validates_presence_of :name`
`end`
`When you say validates_presence_of, the class method in AR::Base is what gets called.
