+++
date = "2016-08-17T07:17:23-06:00"
draft = false
title = "Learning Golang by being Thankful"
image = "/thankfulAppImage.PNG"
description = "Recently I found myself toying around with Golang and I liked it. I decided to give it a full test run on a small project."
+++

# Goal
Recently I found myself toying around with Golang and I liked it. I decided to give it a full test run on a small project. To familiarize myself with Golang, Gin (routing with for Go), and Mgo (mongodb driver) I needed something to build. However, the basic TODO list that is so very common felt a little too boring. One thing I recently read about is how being thankful or grateful can actually help with health and improve productivity. I figure the world has plenty of TODO lists out there and decided to make a web application where a user can keep track of a list of items that they are thankful for much like a TODO list. The twist is that the user can also see items other users are thankful for and add said items to their own list.

[Final Result](/thankful-app/thankful.html)

Thus, I set out to learn a bit more about Golang by creating a web application to help people track items that they are thankful for. But before I dive in, it is important to scope things out a bit more.

# Create Scope Document

The first thing I always like doing which I think many miss out on is creating a simple document that describes the goal/intent/scope of the application that you are building. I didn't go full user story mode as this was more of a quick project than something large. I originally created the document in google drive but below you can find it in markdown.

> ## Thankful
The goal of Thankful is to create a ridiculously easy to use app that allows the user to track things they are thankful for. The user will also have a feed of things other users are thankful for. The user can then share/up vote/repost something in their list from other users.

>The major idea is to have something like a ToDo list app that is very light and can be hosted on heroku or something. The app is for learning Golang as a backend and perhaps react or angular 2 as front end.

> **Tech/Stack:**

> - **Backend:** Golang (gin, mgo driver)
> - **Frontend:** Angular (angular material, font-awesome, animate.css)
> - **Server Host:** Heroku
> - **Db:** mLab hosting mongodb with db named "thankful" and collection of "thankfuls"

> ### Features:
>  1. **Create a Thankful Post:**
>     - User has a single form input upon enter or button tap create the Thankful post and defocus the input (makes mobile easier to use).
>     - Thankful post is saved locally (local data model and storage)
>     - Thankful post is saved to server (creator name randomized using something as a seed)
>  2. **View User's Thankful Posts**
>     - User should see a list of their thankful posts order from most to least recent.
>     - The posts should show the message, when it was posted, and the author.
>  3. **Feed of Thankful Posts**
>     - Icon/Button that shows a badge when there are new posts from other users. Long poll on a timer or something.
>     - When icon/button is clicked, open new view that shows an exit icon/button and a list of other user's thankful posts.
>     - The posts from other users will have a badge showing the number of likes the post has received. When the badge is tapped/clicked increment the posts likes by one on the server.
>     - When the card of the thankful post is tapped/clicked, add the post to the users local list.
>     - Allow user to filter for trending and recent thankful posts.

# Creating a backend with Golang and Gin

The next step I went down is to create the backend. I started with setting up a single route and file but later used Go's packaging to clean things up. Packaging in Go is quite frankly not fun. Go is very opinionated with how packages should work. I will not go into detail here but I spent quite a bit of time scratching my head figuring it out. It is something I would consider when planning to build something larger.

## Gin and Routes with Golang
I used Gin for configuring routes which ended up being about as easy as most would imagine. One thing that was rather nice was being able to setup some middleware for getting a connection to Mongo via Mgo driver and passing the connection along. This was a huge plus in my book for Gin as it was extremely easy and allowed one to create groups of routes that can each have their own middleware. I didn't need to use this feature but was something to note for future projects.

Another nice thing was the ease of setting up CORS with Gin. Again, hooking into the middleware functionality was extremely easy. This pattern while not new has been far easier than past adventures with Node and Express.

## Mgo and Data with Golang
I used Mgo as the driver for MongoDb and Go. There was a bit of a learning curve due to never having worked with bson, json and Go variables. The biggest bit that should save you the most time is to specify an Id before inserting and specifying the bson and json names in the struct/data model.

``` go
type Thankful struct {
    Id bson.ObjectId `bson:"_id,omitempty" json:"id"`
    Message string `json:"message"`
    Author string `json:"author"`
    Likes int `json:"likes"`
    Created time.Time `json:"created"`
}
//----- other code -----
newThankful.Id = bson.NewObjectId()
```

Other than the few issues I ran into with the data model it was quite trivial to use. If you have used any mongo drivers before, you should be right at home.

## Viper and Configuring with Golang
I decided to throw in some a file for configuring the app for production but primarily just for specifying url for the mongodb connection. I went with Viper a config loaded for Go. It was trivially easy. Created a json config file and loaded it up wit Viper to use in the application. Worked the first time which is rare indeed.

## Results
One thing I liked most with Go and the overall mentality of it is how concise everything is. I am not a fan of single character naming which Go really likes but damn in less than 200 lines of code I was able to make a light fully functional rest service. The key here is a similar Express app would have far more files, folders, configuration nonsense, dependencies, etc. Even if go wasn't fast, it still feels light.

I am happy with the results which you can view [here](/thankful-app/thankful.html).
