---
layout: post
title:      "Jobify: JavaScript Project"
date:       2020-12-14 13:39:42 +0000
permalink:  jobify_javascript_project
---


Working on this project was probably the most challenging of them all. Which is something I say when I build each project but in this case it couldn't be more true. JavaScript just made my head hurt but it was such a fun language to work with. The easy part of this project was building the API and the only challening part of that was understanding how to render json for each class method. Once I figured out how to do that the rest was easy.  Another extra thing I wanted to add to my project is adding a nested attribute for my contact table. 

The front end of my project is what made my head truly hurt and what kept me up late at night trying to figure out how it worked. The initial part was figuring out how to use fetch and extract the information from Rails API. Through the fetch method we are able to access a JSON file through the path of the resource I want to fetch. In my case, I had both the positions and contacts API I wanted to fetch. However, this just gave me the HTTP response and not the actual JSON. The HTTP response returned a promise containing the response and we extract the JSON body from that response. Once I got that data I was able to start manipulating that data by creating variables and new instances. I then created to instance classes, Contacts and Properties. In these instance classes, I put a constructor method which allowed me to assign instance properties. I also made three other methods within the Contact and Properites class where I could delete, edit, render and create new objects. 

Another hurdle, I encountered was trying to have my contact and properites appear only when a certian link was clicked. I wanted to be able to do this while only working with one page. This took me a good few hours to figure out. The way I cracked this was by creating an addEventListener which had a 'click' target and passed a function with an if else statement. The if and else statement check if it came from the contact, position or home button depending on the button certain information with be outputed. For example, if the contact button was clicked it would first empty the inner HTML then it would call the that class API which would output the all the contacts. 

Creating new positions or contacts was another feature I added to my app. After creating the respective forms, on the index.js I created to getElementById for each for form and added addEventListern with a 'click' target. When the user submit the form it would each API class and call the respecitve static method. This was definitely a challenging project but very fun to create and learn as I went. 
