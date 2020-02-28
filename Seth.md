# README - Jobs Board (Built on Rails)

This README explains my intent while developing my web project "Jobs Board"

Things I will cover:

* Devise

* Materialize

* Has Many Through Association


## Devise

For __DEVISE__ I kept it very basic by requiring a login when you first navigate to the site. At this point a user can login or signup (featured in navbar). Once logged in users are able to access the full site and land on my static home page. In the navbar the user is able to terminate their login at any time.

## Materialize

For __MATERIALIZE__ I used the navbar formatting to easily link to my Candidate, Job Posting and Job Board Indexs. I recolored it to purple and used <div> classes to clean up the page positioning. I also enjoyed using there default fonts and my forms are much cleaner as a result.
  
## has_many :through Association
  *For more on this please refer to https://guides.rubyonrails.org/association_basics.html*
 
For __HAS_MANY :THROUGH ASSOCIATION__ I set up my controllers so that my job boards had many candidatines and job postings, while my candidates and job postings were associated through the job boards. My primary focus was on the candidate listing jobs they had applied to. I'm still working on it but in theory a candidate could see by region when applying to a job what was remaining from what they had selected. Right now I just have the structure for this and need to work on filling it out.


###Please comment with any questions or suggestions, thanks!
 
