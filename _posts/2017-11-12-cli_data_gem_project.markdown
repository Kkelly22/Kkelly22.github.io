---
layout: post
title:      "CLI Data Gem Project"
date:       2017-11-13 01:48:23 +0000
permalink:  cli_data_gem_project
---


The CLI Data Gem I created is called "Top Netflix".  This gives users the ability to choose from a list of top ranked shows currently streaming on Netflix and see each show's season air date, plot, pros, and cons.  This data is from a Huffington Post article "Ranking The Best Shows On Netflix You Can Stream Right Now".

I watched the youtube demo "Daily Deals" by Avi to get started.  I felt this video provided a very clear and approachable way to tackle this project.  Once my code was written and working with "fake" data, I began integrating the scraped data as the video suggested.  My code contained two classes, a "CLI" class and a "Show" class, both apart of the "TopNetflix" module.  The "CLI" class was responsible for user interaction, and the "Show" class was responsible for scraping and creating instances of the show data.  

### Lesson Learned # 1:
As I was reviewing and refactoring my code (a point where I *thought* I was 99% finished), I began to review the "World's Best Restaurants" gem written by a fellow learn student.  This example clearly showed that my code was *not* utilizing the object structure to the fullest, and was rather depending on the array structure coming from the Nokogiri nested nodes too frequently.  At this point, I adjusted my code.  I created an entire separate class, "Scrape", which was solely responsible for scraping the data.  This isolated the responsibility of the "Show" class to strictly creating instances of shows.  I chose to create all instances of the "Show" class at the start of execution.  Since my "Show" class included the "all" class variable (which kept track of all show instance variables), I was able to utilize the ".all" notation from the start of the user interface by listing each show in "@@all".  I was then able to implement a "find" method once the user chose a particular show.

### Lesson Learned # 2:
This project also gave me better insight into the "require" and "require_relative" usage.  Taking notes from "World's Best Restaurants", I relocated the requiring of the ".rb" files into a "config/environment" file.  This was a more clear cut structure than the structure "bundle gem top-netflix" provided.

### Future Goals
I felt this project cemented many aspects learned in the Object Oriented programming section. In the future I hope to better identify and implement the benefits of object oriented programming *before* I review someone else's code.  I also hope to become better acquainted with the over arching structure of an application, including environments and specs.

