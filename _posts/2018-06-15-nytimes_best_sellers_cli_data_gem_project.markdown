---
layout: post
title:      "NYTimes best sellers CLI Data Gem Project"
date:       2018-06-15 16:01:11 +0000
permalink:  nytimes_best_sellers_cli_data_gem_project
---


This lab was the first project for my portfolio and my thoughts were to create a CLI directed towards finance and the stock market. So, I started creating a CLI that scraped the top ten Stocks of the NYSE. It displayed the description, volume, last quotation and the change (%). Unfortunately, I noticed while scraping that the Nokoguiri wouldn’t scrape certain CSS selectors and my first project was blocked. 

So, I went back to the drawing board!  I then came up with an idea to make a CLI that can display the 15 best sellers of fiction and the 15 best sellers of nonfiction books. This CLI would bring information like name, author, publishers and synopsis. (https://github.com/trtoledo/nyt_best_sellers_cli_app)

The CLI Gem structure was straight -forward. I followed the walkthrough video from the class and used a Bundler from Railscasts (http://railscasts.com/episodes/245-new-gem-with-bundler) to format the Gem with all folders and files necessary to my CLI.

The New Times Best Sellers Books CLI begins by displaying a greeting and asking to the user if he or she wants to check the 15 Best Sellers fiction books list, the 15 Best Sellers nonfiction books list or an option to exit the app.
Once the user chooses a list, it will display that list with the name, number & author of each book on the list. . At the bottom, It asks the user if he or she would like more information about a certain book on the list, if they want to go back to the list menu or an option to exit.
If the first option is the case, the user just has to type the number of the book.  It will then display the publisher and the synopsis next to the name and author.
At this point, the user can go back to the menu where they can choose the list. They can also have more information from another book from the same list and can exit the app.

It was fun coding this CLI Iterating the data scraped from two pages from The New York Time website and being able to create indexed arrays with the 15 best sellers of fiction and nonfiction.  I learned a lot from my original step when I initially was blocked. It was a terrific learning experience.  

