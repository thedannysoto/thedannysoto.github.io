---
layout: post
title:      "Board Game Club - Sinatra MVC Web App"
date:       2020-03-12 19:31:20 +0000
permalink:  board_game_club_-_sinatra_mvc_web_app
---


![](https://i.imgur.com/Y68Civ6.png)

Board Game Club is a web app that allows users to create a board game collections and fill it with many board games. Users can also create a wishlist with games that they want to acquire in the future. Users are also able to look at a list of all of the board games on Board Game Club as well as the board game collections of other users.

Because each user can have many board games and each board game can have many users, I had to create a join table in the ActiveRecord database to keep track of users and the board games that they had in their collections.
```
class UserGame < ActiveRecord::Base 
    belongs_to :user 
    belongs_to :game
end
```


I also had to do the same thing with the wishlist. You can think of the wishlist as a second collection for the user. So I needed another join table that joined wishlists and the games.
```
class WishlistGame < ActiveRecord::Base
     belongs_to :wishlist 
     belongs_to :game
end
```

I ended up using Tailwind CSS to help style the web app. Creating the right styling was what took up most of the time in building the app. I found some templates that used Tailwind and tweaked them to fit my app. I also was able to use a tool called DataTables that used javascript to paginate a table and make it searchable. I used this in my All Games page so that a user could easily find a game by name in the search, or sort any column by clicking on the column header. This also took a while to style to match the web app, but the functionality that it adds is great.

![](https://i.imgur.com/fhr9BXa.png)

The web app gives users the ability to Create, Read, Update, and Delete (CRUD) board games in their collections. There are validations in user input to make sure that the wrong data is not entered and persisted in the database. Users are not able to edit or change another user's collection. When a user deletes a game from their collection, it does not delete it from the database, so other users still have access to that game.

What took the most time in building the app was syncing the small javascript scripts for the alerts and styling the web app through Tailwind. It was good to learn how to use tools like Tailwind and DataTables that can add style and functionality to a web app quickly and efficiently. 
