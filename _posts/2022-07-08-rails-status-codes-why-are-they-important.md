---
layout: post
title:  "Rails HTTP Status Codes - The Importance of Error Handling"
date:   2022-07-08 07:00:55 -0800
categories: jekyll update
---

Rails HTTP Status Codes - The Importance of Error Handling

Why are status codes important in Rails?

Status codes are important because as a client, we are requesting access to one of the 1.88 billion websites (as of Aug. 2021 per statistic.com). When we send our request to the relevant network server via an internet address, a three-digit response code is returned informing the web browser the status of the response. There are five different classes of HTTP status codes:

Class 1 is informational. If a status code of 1XX is transmitted, it means the server is either still processing the information (102) or it is informing the client that the request headers were received and is awaiting the request body (100) or the server is switching protocols and is simply informing the client (101).

![Status Code 100](/my-blog/assets/ErrorCodes/100.png)

Class 2 indicates a successful operation. Status codes of 2XX are transmitted when the server successfully completed a request whether it be created, accepted, reset etc. These are the codes we all want to receive.

![Status Code 200](/my-blog/assets/ErrorCodes/200.png)

Class 3 indicates a redirection. Status codes of 3XX are transmitted when a redirection or a forwarding occurs. This means that the server may be able to successfully process the request, but further steps are needed from the client.

![Status Code 300](/my-blog/assets/ErrorCodes/300.png)

Class 4 is transmitted when there has been a client error. These error codes range from a bad request made by the client (i.e. requesting an ID in the URL that is non-existent) to a request requiring authorization (401) to a forbidden request (403), etc. Please see the list of possible error codes at the end of this blog as Class 4 makes up a big portion of all the status codes in Rails.

![Status Code 400](/my-blog/assets/ErrorCodes/400.png)

Class 5 are server errors. These are transmitted to indicated to the client that the server failed to perform the request. Status codes of 5XX range from internal server error (500), to Gateway Timeout (504), to Network Authentication Required (511).

![Status Code 500](/my-blog/assets/ErrorCodes/500.png)

One thing that I try to keep in mind as a developer is the marketability of the app that I am working on. If for example, I deploy an app that spits out an error code every time the user clicks on the wrong spot or does not fill out a form correctly, it is going to drive user engagement down tremendously and leave my site abandoned. However, we can use certain error codes to interact with the user to ease any conflicts with their requests and the available data. For example, if a user makes a pretty hefty request that requires a bit of leg work from the server, we can transmit a (102) status code to inform the user that the request is being processed. If a user makes a request to a deleted page, we can redirect the user using a (301) status code to display something similar in the hopes that the user finds it interesting enough to continue growing our webpage.

While the aforementioned status codes can be somewhat useful, there are those dreaded 400 codes that are simply unavoidable. In this case, we can output custom error messages instead of the standard ones that come embedded with Rails. A custom error message can shift a user’s thinking from “this stupid app is broken,” to “I made a mistake, why am I so stupid?”

Please see below a list of error codes in Rails. More details explanations for these can be found at: www.railsstatuscodes.com.