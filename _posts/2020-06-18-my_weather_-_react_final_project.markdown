---
layout: post
title:      "My Weather - React Final Project"
date:       2020-06-18 22:48:45 +0000
permalink:  my_weather_-_react_final_project
---


MyWeather is a React web app that communicates with the OpenWeather API to show a user the current weather for a chosen location in the U.S. The user also has the option to see a 7-day forecast for that location. MyWeather uses Redux to store state throughout the app and it uses Thunk to fetch the data from the API.

```
const store = createStore(weatherReducer, applyMiddleware(thunk))
```

I also use Rails as an API to store the locations that a user searches so that I can populate a small menu of recently searched locations. A user can click on a recent location and it will fetch the weather for that location. So a user has two ways of fetching the weather: the regular zip code input on the main weather page and clicking one of the recently searched locations. The Zip Code input validates a user's input and shows an error if the input is not 5 numerical characters. 

The app has 3 routes. The Home or root route shows the title of the app and a navigational button to take the user to the Weather page where they can input a zip code. There is also an About page that gives the user a brief description of the web app. 

```
<Router>
    <div className="App">
      <div id="nav">
      <NavLink to="/" exact className="top-link" >- Home - </NavLink>
      <NavLink to="/about" exact className="top-link" >- About -</NavLink>
      </div>
      <h1 id="my-weather">My Weather</h1>
      <h3 id="tag-line">Look up weather conditions in the U.S.</h3>
      <Route exact path="/" component={Home} />
      <Route exact path="/weather" component={ZipContainer} />
      <Route exact path="/about" component={About} />
      
    </div>
    </Router>
```

One of the challenges with coding this web app was figuring out how to organize the containers and components. The great thing about react is that it is not very difficult to move components around if you need to. As long as you import the component in the right place, you can place it where you need to.  What also changed as the app was built out was which props the components needed. With React, it is important to have the organization of the app clear on the front-end, so that the programming of each component isn't slowed down. 

Thunk makes it really easy to fetch information from a url and then send the info to the reducer to display to the user.

```
export const fetchCurrentWeather = () => {
  return (dispatch, getState) => {
      fetch(getState().url)
      .then(response => response.json())
      .then(responseJSON => {
        dispatch({ type: 'ADD_CURRENT_WEATHER', weather: responseJSON })
      }).catch(function() {
      })
    }
  }
```
