---
layout: post
title:  "Going Postal With Postman"
date:   2022-06-27 07:58:55 -0800
categories: jekyll update
---

Postman is a tool used to work with APIs. This tool is used to test your back-end “server-side” code whether it be in Ruby, Node, PHP and make sure that the pages you are writing are working properly.

Start by choosing which method you are going to use. Put in path (or URL) to which you are making the request:

![Initial GET Request](/my-blog/assets/GoingPostal/initialGET.png)

You can specify which key value pairs you want to add…in this case, which ones you want to GET.  For this case, we’ll make a request to GET the entire table of data.

![Initial GET Request](/my-blog/assets/GoingPostal/GETresult.png)

You can check the status of the request and see that we’ve received a Status of ‘200’ meaning it was successful. You can also see that it took 36 milliseconds to receive a response and the size of the data that was fetched is 6.61KB.

![Initial GET Request](/my-blog/assets/GoingPostal/ResponseStatus.png)

Great! We can see that our request was successful. So what else can we test?

Let’s try making a POST request to our database using Postman. For this to work you’ll want to change your method to ‘POST’, and again specify the path. In this case we’ll want to post our new data to the same ‘dogs’ server. You’ll want to specify the Headers. In this case we’re going to use Content-Type and application/json because we’re sending data to the database in JSON format.

![Initial GET Request](/my-blog/assets/GoingPostal/Headers.png)

You can enter the information you're POSTing using the form-data option as seen below.

![Initial GET Request](/my-blog/assets/GoingPostal/KeysFormData.png)

I prefer using the raw option to format the JSON data I'm sending as seen below.

![Initial GET Request](/my-blog/assets/GoingPostal/RawBody.png)

And as you can see by the response, this shows that the POST was successful.

![Initial GET Request](/my-blog/assets/GoingPostal/POSTresult.png)

Let's check our database in the back-end to make sure that it received the information we sent. As you can see below, it was successful.

![Initial GET Request](/my-blog/assets/GoingPostal/BackEnd.png)

Wait! Brian is actually a white Labrador and is actually 8 years old in dog years. Let’s edit out information. For this we make a PATCH request using the same headers and editing the information like so:

![Initial GET Request](/my-blog/assets/GoingPostal/FailedPATCH.png)

Hmm…looks like we’ve received a blank { } as a response. Checking our database reveals that nothing was changed. Nothing happened because in order to complete a PATCH request we need to specify the ‘id’ of the object that we’re editing. In the path, make sure to include the ‘/id’ in order to pinpoint the object. In this case, the id is ’21’:

![Initial GET Request](/my-blog/assets/GoingPostal/SuccessfulPATCH.png)

Looking good. Our response in JSON format shows the updated data to his breed and age. 

Here are some tips to make your life easier using Postman.

You can create “Collections” when you are working with the same database often. Do this by clicking on “Create Collection.” Name your collection; for this example we’ll be naming it “Dog Collection.” 

![Initial GET Request](/my-blog/assets/GoingPostal/DogCollection.png)

Now you can save the methods and URL paths you are using to this collection so that you don’t have to change each field/method every time you want to run a different request. In this example we’ll be saving a “GET” request to the path http://localhost:3000/dogs. 

![Initial GET Request](/my-blog/assets/GoingPostal/CreateGETRequestCollection.png)

Now let’s simplify our lives even further. Say you’re working with multiple URLs. Who has the time to memorize every single path you’re working with? Postman lets you save the URLs as “variables” so that you can just type in the variable name and it will point to the path specified. All you’ll need to remember now is the keywords you used to name your variables. And if you forget those, you can simply look at the list of variables you’ve saved in either your Collection, Environment, or Globally!

![Initial GET Request](/my-blog/assets/GoingPostal/AddVariableCollection.png)

Awesome, now we've added a few shortcuts to our environment.

You know what, I don’t like Brian very much (he’s a little annoying). Let’s delete his information from our database. For this, we use the DELETE method, specifying his specific ‘id’ in the path. Note that we are abel to use the variable we previously defined "dogsURL" and all we need to do is add the /'id' in order to specify the path:

![Initial GET Request](/my-blog/assets/GoingPostal/initialDelete.png)


You’ll see after hitting SEND that we receive empty { } as the response, indicating that his information was destroyed. Looking at our database, this is confirmed.

![Initial GET Request](/my-blog/assets/GoingPostal/SuccessfulDelete.png)

Postman is a priceless tool when it comes to working with APIs and I highly recommend using it to test your data. Please check out the video below for a much more in-depth guide to Postman.

<iframe width="560" height="315" src="https://www.youtube.com/embed/VywxIQ2ZXw4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

