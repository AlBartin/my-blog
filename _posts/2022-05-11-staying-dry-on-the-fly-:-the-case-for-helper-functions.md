---
layout: post
title:  "Staying Fly on the Dry: The Case for Helper Functions"
date:   2022-05-11 07:58:36 -0700
categories: jekyll update
---

### “You have to literally read every line of code to understand what’s happening here." - Cohort Mate 

What is a Helper Function? A Helper Function is a function created in your code that you are able to call within other functions to perform tasks that are otherwise repetitive. These functions are helpful not only to ease up re-writing the same code multiple times, but to also help you as a programmer think about what you want your code to do in building blocks rather than breaking it down to individual steps per line. You can focus on the current function that you are working on without without worrying about the individual steps of the other function. This is another way of keeping your code legible, comprehensible, and DRY (Do Not Repeat Yourself).

Example: Say you have a program that is meant to calculate the valedictorian of a graduating class (i.e. finding the student with the highest gpa), but all that you have is the student’s letter grades available. You need to perform multiple tasks to achieve this. Let's first build a function that produces a student's gpa. Let’s break into steps:

1. You need to calculate each individual student’s Grade Point Average.
2. We take each letter and convert that to an integer.
3. We take all of the integers and calculate the average by dividing the total sum by the total number of integers.

Let’s start with this example:

![GPA Function](/my-blog/assets/image1.png)

Here we are performing two things within this function. We are taking an array of letter grades, looping through the array and converting each value within each index into an integer using boolean expressions, while also taking that new value and pushing it into a new array of integers. AFTER that loop is complete, we are taking the array of integers and adding all of the values to come up with our total points that THEN gets divided by the total number of indexes to return this student’s gpa. Are you winded yet? How can we make this drier?

Let’s think of this in blocks of functions. What I mean is, look at your code and try to identify which lines are working together to perform, not the entire function, but portions that then contribute to the performance of the entire function. In this case we can see that our first for loop is producing a new array. Let’s take that and make it its own function.
![](/my-blog/assets/image2.png)

Here we’ve called this new function gradesIntegerArray and set the parameter as gradesLetterArray. Now how can we make this even drier? Within each boolean expression, we are assigning a new variable with the integer that we are then pushing into the new array that we’ve created. But if we are looping through the array, can we just remove the variable and push the integer itself.
![](/my-blog/assets/image3.png)


Great! Now let’s call this helper function within our main gpa function.

![](/my-blog/assets/image4.png)




Uh Oh! We’ve run into an issue here! Our second for loop was using the array being returned from the previous for loop to perform its job (or …function). How can we take take this wrench out to get our gears running again?

![](/my-blog/assets/image5.png)
Let’s take our second for loop and make it its own function. 

![](/my-blog/assets/image6.png)

For this function we are going to pass it the array that is being returned from our first function gradesIntegers as the parameter. Great! Now we have this little matryoshka to work with.


![](/my-blog/assets/image7.png)


Let’s clean it up a bit to help us better understand the logic with what’s happening here here.

![](/my-blog/assets/image9.png)

You’re probably thinking, “ok, so what? How is this helpful?” When we were building our functions out, it helped us break our entire code out into steps or in other words building blocks. We have our gradesIntegers function that takes in an array of letter grades and spits out an array of integers for us to work with. We have our sumGrades, which takes an array of integers as its argument and spits out the total sum of grades. Then finally these two functions are nested into the gpa function which actually calculates the grade point average we are going to later use to find the valedictorian. But that’s a topic for a later blog.









Cleaning up your code and assigning variables with helpful names helps the next person who looks at your code follow along with the logic behind what you are trying to produce.

