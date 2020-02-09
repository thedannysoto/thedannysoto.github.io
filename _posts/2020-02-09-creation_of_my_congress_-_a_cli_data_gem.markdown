---
layout: post
title:      "Creation of 'My Congress' - A CLI Data Gem"
date:       2020-02-09 19:26:50 +0000
permalink:  creation_of_my_congress_-_a_cli_data_gem
---


The initial idea of My Congress was to prompt the user for an address and return the U.S. Senators for that state and the Congressional Representative for the district associated with the address. I found a website that provided me with the information I needed and started to build the scraper tool to retrieve the data. I tried using Nokogiri, but the particular website I was using had a meta-refresh that Nokogiri couldn't handle. Basically, after providing the website with the address, if would redirect to a new website, pause, and then proceed to the final website with the information. For some reason, Nokogiri would get stuck at the initial website which would not have the information I needed. I had to use Selenium Webdriver to scrape the website instead. Selenium opens a web page in the background and waits until the chosen element appears on the web page. Once Selenium was able to retrieve the final page, I then passed it off to Nokogiri to retrieve the elements I needed. Figuring out how that I needed to use Selenium instead of Nokogiri was one of the biggest hurdles I had early on in the building process. 

Once I was able to get the correct information, I organized it and presented it to the user. I then added a feature that could show the user what the upcoming election dates and types where for their location. This process was easier because I only needed to provide the website with the user's state, and not the complete address. 

The third feature that was added was an option to see the current headlines in U.S. politics. This option returns a list of headlines, a small blurb about the headline, and the source website with the complete article. I thought about adding a way for the user to see the complete article through the CLI gem, but each source website was from a different news source, so there would have to be a scraper for an unknown number of source websites. I decided that that would be outside of the scope of this gem.

The final feature of the CLI gem was an option to see upcoming Senate and House bills. The user is able to see the bills name and sponsor, and they have an option to read a summary of the bill, if available. The third and fourth features don't require an address, so there is no user prompt if they choose those options.

After adding the features I cleaned up the code and used the Colorize and TTY-Prompt gems to clean up what the user sees when using the CLI. One of the steps towards the end that gave me some trouble was figuring out how to upload the gem to RubyGems.org and run it through my terminal. I had to configure the gemspec file in a certain way and fix the $PATH variable on my computer, but I got it working in the end. 

One of the weaknesses I see in My Congress is that through the four features it ends up scraping four different websites. That means 4 times the possiblity of something breaking. But it also meant 4 times the practice of working with Selenium, Nokogiri, and scrapers, so I think it was worth it for the coding practice. I think a very important step was going back through the code and cleaning it up. I didn't really map out how the program would work initially. I just ran with the first ideas I had. That meant quick early progress, but also messy code. I had to take the time to organize the code into the relevant methods and make sure everything communicated correctly. It made the code much more readable and easier to fix or manipulate in the future. 
