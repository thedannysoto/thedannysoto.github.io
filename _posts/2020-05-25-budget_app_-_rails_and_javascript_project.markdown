---
layout: post
title:      "Budget App - Rails & Javascript Project"
date:       2020-05-25 12:15:58 +0000
permalink:  budget_app_-_rails_and_javascript_project
---


My Rails and Javascript project was creating a small Budget App. The main section of the page contained a table that I made in Tabulator. Tabulator is a javascript library that allows the user to create a  table that is highly customizable. I also incorporated Moment.js for date information and TailwindCSS to help with styling the page. 

The Rails API has 3 models: Account, Category, and Transaction. Accounts have many Transactions, and many categories through Transactions. Categories have many Transactions, and many Accounts through Transactions. A Transaction belongs to an Account and belongs to a Category.

```
    def index 
        transactions = Transaction.all 
        render json: transactions, status: 200
    end
		```

Two areas that took up a lot of time early on in the coding process were styling and arranging the page with Tailwind and customizing the table in Tabulator. This was the first time using Tabulator, so there was a small learning curve. But everything that I needed the table to do was explained in the Tabulator documentation. 

```
const table = new Tabulator("#transactions-table", {
```

The next step was to create the Javascript classes to receive the correct information from the Rails API. I also needed to code event handlers to update the relevant portions of the page when information was updated by the user. Users have the ability to create, read, update, and destroy transactions  in the app. Transactions are coded to particular accounts in the User's budget. A User can also create categories through the transactions that are entered. The API will find or create categories by the name entered by the User.

Another hurdle I had to overcome late in the project was the logic of the budgeting section of my app (handled by the Rails API). I didn't fully plan out how certain elements would update after User-entered input, and that was a mistake on my part. I had to figure out how to update multiple elements from one User change. 

I took inspiration for my project from YNAB, a budgeting software that I use. I wanted to model my interface sections after some of those in YNAB.
