# README

# Controllers

### What is a Controller?
You can think of a controller as the middle man of a MVC application. The controller understands what it needs from the model, but allows the model to most of the work. The controller also knows what kind of view it would like to create, but allows the view to create what we will be seeing on the page. The controller is named well, in essence it is 'controlling' the app and telling everything else what to do and how to do it. 

### Keeping the controller clean.
The controller does not need a lot of code to work effectively, in fact the less logicical code in the controller the better it is for your app. The different view pages is where all this logical code should live, the controller is simply directing the app where to find this code. 

### Naming is important!
We all know that Rails is some kind of magic, doing things behind the scenes of our app and makes things simple for us. Beacuse Rails is looking for a certain way of naming, there are a couple things to keep in mind:
1. Controller class names use CamelCase and have Controller as a suffix. 
2. The Controller suffix is always singular. 
3. The name of the resource is usually plural.
4. Controller actions use snake_case and usually match the standard route names Rails      defines (index, show, new, create, edit, update, delete).

Something to keep in mind is what the controller does once it has finished running through all the lines of code. Once Rails gets to the end of the controller, it grabs all the isntance variables from the controller and sends them over the view file _which is named the same thing as the controller action_ and which lives in a folder named after the controller. If you save your files in a different folder or hierarchy, you’ll have to explicitly specify which ones you want rendered.

### Redirecting and Rendering
Although Rails will implicitly render a view file that is named the same thing as your controller action, there are plenty of situations when you might want to override it. A main case for this is when you actually want to completely redirect the user to a new page instead of rendering the result of your controller action.
Redirects typically occur after controller actions where you have submitted information. An example of this would be when you create a new 'thing'. We will typically want to see what was created, so we can redirect to the Show view for that 'thing'. This is typically the best course of action if our 'thing' is successfully created. But what if our 'thing' was not successfully created?

This is where our rend option comes in. We can tell our controller to render the page again, possibly with some error styling messages, so the user can attempt to create the 'thing' again. An example of this in code would look similiar to this:
```ruby
    def create
      # code here to set up a new @post based on form info
      if @post.save
        # code to set up congratulations message
        redirect_to post_path(@post.id) # go to show page for @post
      else
        # code to set up error message
        render :new
      end
    end
```

### Params
Params is an alias for the parameters method. Params refer to the parameters being passed to the controller via a GET or POST request. Params is a hash and acts just like a normal Ruby hash and contains the parameters of the request, stored as :key => value pairs. So how do we get the ID of the post we’re asking for? params[:id]. You can access any parameters this way which have “scalar values”, e.g. strings, numbers, and booleans for example.
