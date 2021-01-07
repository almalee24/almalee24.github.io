---
layout: post
title:      "Asynchronous Behavior & event.preventDefault()  "
date:       2021-01-07 14:33:17 +0000
permalink:  asynchronous_behavior_and_event_preventdefault
---


In summary, event.preventDefault() method gives the you the ability to prevent a browser’s default behavior for events. For example:

```
static renderSearch(){
        const contactContainer = 			document.getElementById("content")
        const searchCard = document.createElement('div')
        searchCard.innerHTML += this.filterForm()
        contactContainer.appendChild(searchCard)
        document.getElementById('search-form').addEventListener("submit", e => e.preventDefault(Contact.filtered))
}
    
static filtered(){
        let names = document.getElementsByClassName("contact-card")
        let word = document.getElementsByName("search-filter")[0].value
        for (let i = 0; i < names.length; i++) {
            let match = names[i].innerText.split(' ').filter(name => name.toLowerCase() == word.toLowerCase())
            if(match.length == 0){
                names[i].style.display = 'none'
            }
         }
    }
```

The example above shows a filter method for contacts. There’s a submit event listener in the search form that calls the filtered static method.  Without the event.preventDefault(), the static filtered method completely clears out all the contacts when the for loop is completed. The default behavior of the form is to reload the page but that’s not what the filtered method was intended for. The method was intended to filter out all the contacts that don’t match the input. To accomplish this I pass the event into my filtered method and added event.preventDefault() to catch the submit event and prevent the page from reloading. 

Using fetch requires one argument, the path to the resource you want to fetch. For my project, I used http://localhost:3000/connections and http://localhost:3000/positions respectively. This returns a promise that contains the HTTP response. The promise is an object that gives the completion or failure of the asynchronous operation. If the promise is successful we can extract the JSON body from that response using the then() method. This method requires two arguments and  also returns a promise with a response.

```
static addConnections(){
        fetch("http://localhost:3000/connections")
        .then(resp => resp.json())
        .then(connections => {
            connections.forEach(connection => {
                const{id, contact_date, take_away} = connection
                new Connection(id, contact_date, take_away)
            })
        })
    }

```

JavaScript is a coding language that preforms only one thing at time which can be a problem when it you’re requesting data from an API like I did in for my project. Using asynchronous behavior always you to make long request without blocking anything else. 
