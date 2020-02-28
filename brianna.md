So first thing is the work flow of an MVC( Model, View, Controller)
-The model is the thing that talks to the database and returns data
-The View is the thing that generate the display that the user interacts with
-The controller is basically the middle guy between the model and view

So the user goes to the application and the rails router takes them to the root page

From there they have options. Let say theres is a Billboard model 

This first page is the Billboard index(where all billboards are displayed)

Okay so knowing that, lets say they want to view one of these billboards

When they click on the "View Billboard" link it will then send a request to a controller

The billboards controller is then gonna go "Okay, the path is billboard#show". He is then gonna look at the methods he has and find the one that matches show. Show is then gonna give the model an id number for a billboard and ask for information. The model goes Oh okay, leans over and goes "psst, database im looking for the information of a Billboard with an id of 1" The database then hands over this table with all the data the Billboard with the id of 1. Then the model hands the table to the controller. Controller goes, "Great!" and hands the information to the view. (_html.erb). Who puts that information on to the page as requested. Now thats just for show which is a get method.

Let say the user clicks on "New Billboard". Here the controller uses this new_billboard_path and goes okay so billboard#new then looks for his new methods. In here theres is usually "@billboard = Billboard.new" This is just creating an empty object that he can send into a form (view) in the view the user fills out all of the fields then hits "Create Billboard". When this Create Billboard is clicked. It tells the controller "Hey i got some info that needs to be put into the database" He takes this information and goes okay... this is a post method that needs to go through billboard#create. Finds the method create puts the information in there and sees if the right information is there or not. If it is there it gets sent to the model who gives it the database. Then the database gives it an id and a place in the table.
Now lets say there is something wrong with the information that the method create gets. Create is gonna push back and tells the controller, "hey man, this isn't right. Take it back to new and get it fixed" Where the controller takes it back to new and says "FIX IT"

Now update is a mix of show and create. When the user clicks "Update Billboard" the viewer yells "we got an update! id number 1!" (edit_billboard_path(@billboard)) The controller goes okay so billboard#edit... finds the edit method then asks the model , hey whats the table for billboard with id of 1. Model gets the information from the database and hands it back. Once edit has this information he is able to send it to an edit viewer that fills the fields with the current information and lets the user change it. When the user clicks the "Update Billboard" The controller takes this new information and gives it to his update method to get checked out. Just like the create, if it checks out he sends it back to model says heres the new information and gives it to the database say hey replace the values in billboard 1 with this new stuff the gives the controller a thumbs up and then goes to a determined view. Maybe the billboard_path(@billboard) which is the show page

The last of the CRUD actions is the Destroy Method which is the show path except with the method of delete. He takes this billboard id and finds his destroy method which then tells the model, hey do away with billboard 1. He then looks at the Database and goes "Billboard 1" then slowly drags his finger across his neck and winks. The database says rodger and winks back, then the model gives the controller a thumbs up and he goes to some other viewer. 

