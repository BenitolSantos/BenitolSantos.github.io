---
layout: post
title:      "Textbook-Organizer"
date:       2020-03-11 01:30:53 +0000
permalink:  textbook-organizer
---


Woo this took WAY TOO LONG.

Originally someone put the idea in my head that I should put a progress tracker, which wasn't even needed. That set me back about a month.

![](https://media1.tenor.com/images/0d737848e012df23c93b9c30c38b21c6/tenor.gif)

Then winter vacation and the changing of the project leaders, led to few unorganized study groups and constant cancellations. Not blaming them, its hard when people change whose in charge.

So I scrapped it for a minimum viable product. Then I had to scrap Admin Users for a minimum viable product.
I bit off more than I could chew.  I should have done created what I wanted first then added.

Ok so rails is different from sinatra in that you need to use "rails magic" and use a routes page.
Rails magic is easier html shortcuts.

For the most part, its basically the same.

I made an textbook library/organizer with some cool nifty new tricks.

So far, everyone can create and destroy and edit textbooks.

Here's my models.

# **Subjects**
# 
# **UserSubjects**
# 
# **Textbooks**
# 
# **Users**

And now I learned some nifty tricks like Facebook implementation, password encryption, forms and partials.

Heres some of the requirements. 


 [X] Include signup (Remember bcrypt salt)
  <br>

- [X] Include login
  <br>

- [X] Include logout
  <br>

- [X] Include third party signup/login
  <br>

- [X] Include nested resource show or index (routes.erb 
  * URL e.g. categories/3/posts -> class/3/textbooks/
  <br>

- [X] Include nested resource "new" form ()
  * URL e.g. categories/7/posts/new)
  <br>

resources :attractions do 
  resources :rides
end

/attractions/1/rides/new <- just rides/new associated


- [X] Include form display of validation errors
  * form URL e.g. /posts/new)
  <br>

Confirm:
- [X] The application is pretty DRY (partials and layouts most def)
- [X] Limited logic in controllers
- [X] Views use helper methods if appropriate (scope method is a helper method)
- [X] Views use partials if appropriate
