---
layout: post
title:      "TrollyWingz: React & Redux Project"
date:       2021-01-27 07:43:39 -0500
permalink:  trollywingz_react_and_redux_project
---


This was by far my favorite project to work on. There were hundred millions times were I got stuck, didn't know what I was doing and then became an slight expert in the subject. This project is the culmination of the months of learning at Flatiron and the realization that I learn best when I dive head first and just fake it till I finally understand. Which brings me to TrollyWingz, a grocery delivery app built with a Ruby on Rails API backend and React frontend. 

On the backend of my project, I started off with Company and Goods table. Company has_many :goods and Goods belongs_to company. Once I structured the controller and serializer for both tables and seeded data I started working on the front-end. The front-end is what gave me more trouble as the project progressed. The app had one HTML page to render my  react-redux application and  I used various state components to structured the data after it was fetched and passed correctly. For example, I fetched all the companies on my back end by doing the function belown on my actions folder. 

```
export function fetchCompanies(){ 
    return(dispatch) => {
        fetch('http://localhost:3001/companies')
        .then(resp => resp.json())
        .then(companies => dispatch({
            type: 'FETCH_COMPANIES', 
            payload: companies
        }))
    }
}
```

Once the information was fetched from the url and the response was converted to JSON, the final then method uses  connect to dispatch companies allowing them to be accessed by the components. The 'FETCH_COMPANIES' calls the company reducer and returns an array of the companies fetched. 

```
export default function companyReducer(state = [], action){
    
    switch (action.type) {
        case 'FETCH_COMPANIES':
            return  [...action.payload]
        case 'ADD_COMPANY':
            return [...state, action.payload]
        default:
            return state 
    }
}
```

I then created the store using that information passed by the reducer. In my Companies Container, I used mapStateToProps to extract information from the store. For this container the information was the array of companies. 

```
render(){
        return (
            <div className="wrapper">
                <Switch>
                    <Route exact={true} path='/stores/new' component={CompanyInput}/>
                    <Route exact={true} path='/stores/:id/storefront' render={(routerProps) => <CompanyShow router={routerProps}/>} />
                    <Route exact={true} path='/stores' render={(routerProps) => <Companies {...routerProps} companies={this.props.companies.companyReducer}/>}/>
                </Switch>
            </div>
        )
    }
```

In the return method I delcared routes and used switch to ensure that routes were render exclusively. Then I passed props to the componentes render by the routes. For the index route that shows  all companies I called the companies component.  In there I iterated through companies using map and render indivual divs that included company name, logo, background image and features. You could click on the company and it would take you to the store front. By doing this we are now in the Company Show component iterating through all the individual company information and goods. 


I also created user signin. login and a shopping cart. This required both backend tables and controllers but also required more fetches and stateless components. This was very challenging project but one that has helped my grown so much in my skill. There's still so much work to be done and I'm excited to continue developing this app further. 
