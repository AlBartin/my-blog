---
layout: post
title:  "Staying DRY on the Fly: React...ing a fool!"
date:   2022-05-25 07:58:55 -0700
categories: jekyll update
---

In my previous blog post I wrote about the importance of using helper functions to make our code more DRY. Let's remember some key points from that post:

1. Creating helper functions with informative names helps not only ourselves, but also the next person to look at our code.
2. It's especially helpful when attempting to solve algorithms when we use our helper functions as building blocks.

Originally, I was going to deploy my GPA Calculator app and apply some sweet CSS and html to have a working app, but then React peaked it's beautiful mug into my life and decided to turn it upside down. Learning React was like trying to crawl through Charlotte's Web. Once I thought I had a grasp on things, I forget to include the holy {curly braces} and break my entire code. But alas, I continued to think of ways to improve my GPA Calculator app and refactor my vanilla javascript code into React components.

So I created my React App in VS Code which renders the following:

![Original React App](/my-blog/assets/ReactApp.png)

And I thought great, let's create some components. I put together the following:

![Original GPA](/my-blog/assets/OriginalGPA.png)

* Gpa.js
* StudentPage.js
* StudentForm.js
* Valedictorian.js

Each component will perform a different function for this app. So I began refactoring my original code and inserting it into these components, but I could not get my code to compile. I worked on this for hours and found myself in a similar situation as Charlie trying to talk about the mail before the sun set in Philadelphia.

![Crazy Charlie](/my-blog/assets/CrazyCharlie.gif)

So instead, what I did was apply some wisdom I received during Phase 2 of my coding bootcamp at Flatiron. And that is to map out a plan of attack before diving into writing code. So I pulled up our beloved DrawIO extension in VS Code and began drawing. I came up with the following "map" of my React app:

![Original Map](/my-blog/assets/OriginalMap.png)

Then I started thinking about where I want to add our State hook and what to send as props down to Child components. I put State in the top Parent Component "App.js." The reason for this is so that I can send the student array I pull from my data as a prop to StudentPage.js to be rendered when the app loads. Then, I decided to send a handleSubmit function as a prop to StudentForm.js in order to pull all the data from the form that will take in new student information. StudentPage.js will also send {name, classes, grades} as props to Gpa.js where they will be used to calculate a student's gpa with simple math. Then Gpa.js will send the resulting {name, gpa} to Valedictorian.js where a function will sort the student object and return an array of students with the highest GPA first and designate them as the valedictorian for the class.

![Better Map](/my-blog/assets/BetterMap.png)

Doing all of this planning and mapping is very helpful in determining how we want our web of components to communicate with each other to ultimately create a functioning ecosystem (app). Stay tuned for the next episode of Staying DRY on the Fly where I actually see if I can get all of these components working without breaking (...down in tears).