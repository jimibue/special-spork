# Routes on Rails!

### What are they?

Routes are HTTP methods that your computer and a server use to communicate with each other over the internet.
More specifically, routes are linked to what we call CRUD actions in our Rails controllers.

1. C - *Create (Post)*
2. R - *Read (Get)*
3. U - *Update (Put)*
4. D - *Destroy (Delete)*

These CRUD actions directly relate to the Model/View/Controller pattern of app design commonly used in Rails.
Specifically, routes link the User directly to the Controller arm of the MVC framework which handles all of the CRUD operations for our app. 

```
  def index
  end

  def show
  end

  def new
  end

  def create
  end

  def edit
  end

  def update
  end

  def destroy
  end
```

This is a sample of what a Controller would look like in an MVC style application.
Our Routes take User requests (what you type in the search bar), finds the correct route for what you've chosen, then leads you to that corresponding method on the controller. 

Let's say you wanted to see the homepage of a website. You'd probably be looking to visit the Index of that webpage which has likely been labeled as the "root" or first page a user should see upon loading. By simply typing in the url web address, a request (GET) would be sent to the Controller for that webpage, the controller would then grab the corresponding View (remember our MVC model?) and then return that View to the user.

This process repeats indefinitely for all our CRUD actions like Create, Update, Destroy, New, etc. 
Each of these controller actions corresponds to one of our HTTP verbs (post, get, put, delete), with each having it's own path (url) *and* "controller_name#action".

Every Rails app has a Routes file that houses the given routes for our controllers. One way to quickly consolidate all of these routes into one line is by using `resources :controller_name` which will build out all of our CRUD actions.

