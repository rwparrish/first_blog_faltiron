---
layout: post
title:      "Finding the joy in sloving one problem at a time"
date:       2020-05-16 16:53:07 -0400
permalink:  finding_the_joy_in_sloving_one_problem_at_a_time
---



I just finished my first web application. After programming fulltime in an online boot camp for a month and a half, it feels amazing to reflect on how much I have learned and grown as a programmer. While working with Sinatra and ActiveRecord for the first time I can’t help but feel that I don’t yet really understand the power these tools bring. However, programmers that have been programming for years still don’t know everything that these tools can do. Again, the point here is that programming is about being OK with not having a perfect understanding of all the tools available to you. Programming is about being able to allow yourself to play and learn as you build. You’ll come across all kinds of bugs, logic puzzles, and frustrations when programming. In this post, I’d like to discuss one of those instances. 

I found that while implementing some ActiveRecord validations I was having some trouble getting error messages to show. Eventually, I was able to realize that redirecting to a route which would then render the view I wanted was creating the issue. When redirecting the error messages were not persisting. The solution, break convention, and render the view instead. The lesson, becoming too rigid, and relying too much on convention can become a hindrance. Convention is valuable and has its benefits to be sure. However, as with all things in life balance is key!

![](https://media.giphy.com/media/13HgwGsXF0aiGY/giphy.gif)
