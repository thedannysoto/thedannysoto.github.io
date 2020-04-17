---
layout: post
title:      "Fresh Wash - Rails Portfolio Project"
date:       2020-04-17 23:00:16 +0000
permalink:  fresh_wash_-_rails_portfolio_project
---



Fresh Wash is a car wash web app built on Rails. It allows users to create logins with email or through Facebook authorization. Users can add cars to their home page, edit or remove cars, and wash cars with one of the car wash packages (there are 4 in total). The app can also show users their order history with each wash purchased linked to the cars registered.

User creation through Facebook is handled by the Omniauth gem. User creation through the web app has different validations that check each field for valid input. Invalid input refreshes the sign up page with an error message at the top of the screen.

```
validates :name, presence: true
    validates :email, presence: true
    validates :name, length: { minimum: 2 }
    validates :email, uniqueness: true
    validates :email, format: { with: URI::MailTo::EMAIL_REGEXP } 
    validates :password, :password_confirmation, presence: true
```

The app uses 4 different models: User, Car, Package, and Wash. Users can have many cars, and a car belongs to a user. Washes are a join table that join Cars and Packages. So a car can have many packages through washes, and a package can have many cars, through washes. 

```
class Car < ApplicationRecord
    belongs_to :user 
    has_many :washes 
    has_many :packages, through: :washes
```

Washes for all cars are tracked on the Order History page. A user can check the page and see washes for all cars ordered by most recent first. Through two different scope methods, a user can reorder the table by price (lowest to highest) and group each wash by car.

```
default_scope { order(updated_at: :desc) }
    scope :ordered_by_price, -> { joins(:package).reorder('packages.price').order(updated_at: :desc) }
    scope :ordered_by_car, -> { joins(:car).reorder('cars.make').order(updated_at: :desc) }
```

I used tailwind css to help style the page. Most of the styling is done as a class for each element as opposed to a separate css stylesheet. I think styling the page took up the biggest chunk of time followed by making sure that everything was routed correctly. 



