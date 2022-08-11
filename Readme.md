# MAPTY PROJECT PLANNING

1. USERS STORIES
2. FEATURES
3. FLOWCHART
4. ARCHITECTURE

//////////////////////////////

**USER STORIES**

The user's stories is basically the description of the application's functionality from the user's perspective. The purpose of the user's stories when all put together is to provide a clear picture of the application whole functionality. There are different formats used to write user stories but the most common one is to write sentences. Common format: As a [type of user], I want [an action] so that [a benefit]. This type of format answer three W's questions; WHO? WHAT? AND WHY?

In the case of the mapty project;

1. As a user, I want to log my running workout with location, distance, time, pace and steps/minutes (cadences), so I can keep log of all my running.

2. As a user, I want to log my cycling workout with location, distance, time, speed and elevation gain, so I can keep log of all my running.

3. As a user , I want to see all my workouts at a glance, so i can easily track my progress over time.

4. As a user, I want to to also see my workouts on a map, so i can easily check where i work out the most.

5. As a user, I want to see all my workouts when i leave the app and come back later, so that in can keep using the app over time.

Although, different people will come up with different user stories for the same application but what is important is that we can use user stories to describe what exactly the app will do. NOTE , As a developer you have to put yourself in place of the user so as to come up with user stories (You will think a lot so as the derive your FEATURES from it)

////////////////////////////////////////////////////////////

**FEATURES**

Features is always derived or generated based on the user stories. For example, based on
the user stories from Mapty project, we have some features already;

_(Based on the first user stories 1. )_

- Map where user clicks to add new workout (best way to get location coordinates)
- Geo-location to display map at current location (more user friendly)
- Form to input distance, time pace, step/minutes

_(Based on the second user stories 2.)_

We will need the same features just that the form input will be different

- Form to input distance, time, speed, elevation gain

_(Based on the third user stories 3.)_

- Display all the workouts in a list

_(Based on the third user stories 4.)_

- Display all the workouts on a map

_(Based on the third user stories 5.)_

In a real world we will have a an account where user's data will be stored but in our case we will use the localStorage API in the browser to store data.

- Store workout data in the browser using localStorage API.
- On page load, read the saved data from local storage and display both on the map and list.

///////////////////////////////////////////////////////

**FLOWCHART**

Flowchart basically what our application should. It contain what the features entails in a more visual or interacting way.Also, it contains how the different path going to interact with each other; like which feature should come first and which one should come last, and also how data flows across the application. Check the picture attached to the repository. ![](Mapty-flowchart.png)

**ARCHITECTURE**

NOTE: We don't need to have final or perfect architecture before we start implementing our codes. so we can first write your codes and then refactor it later into a nice and clean paradigm.

## Project Architecture

In this Mapty Project we will be using the OOP paradigm in which we will have a class for each of the data object and the functionality of object.

**Data Architecture**

We are going to have a parent class the `workout` that will contain the common properties like distance, duration, ID, Coords and date for both child `Running` and `Cycling`. And on the parent class is where they will inherit these properties. Each child will have their own unique properties. From the child classes, we can now create different instances.
For example;

```
Data Architecture

// PARENT CLASSES
class Workout {
  date = new Date();
  id = (Date.now() + '').slice(-10);
  constructor(coords, distance, duration) {
    this.coords = coords; // [lat, lng]
    this.distance = distance; // in km
    this.duration = duration; // in min
  }
}

// CHILD CLASSES
class Running extends Workout {
  constructor(coords, distance, duration, cadence) {
    super(coords, distance, duration);
    this.cadence = cadence;
  }
}

class Cycling extends Workout {
  constructor(coords, distance, duration, elevationGain) {
    super(coords, distance, duration);
    this.elevationGain = elevationGain;
  }
}

```

Now the **Functionality Architecture**

This basically creating a function for different event or activity in the application. Like the data architecture, we are going to create a class called App which wil hold all the functions as methods. Now, according to the user stories we are going to have these methods for the event that will happen in the application;

`_getPosition()` Because we want the browser to get current position of the user using Geolocation API as soon as the page loads, therefore, we are creating a method `_getPosition()` in the constructor function which will trigger the `_getPosition()` as soon as the page loads.

As we receive the the position we want to load the map based on the position gotten from `_getPosition()` method. Therefore, we are going to have a `_loadMap()` method.

And as the user clicks on the map, we want to call a method called `_showForm()` for user to input data.

As the user changes from running to cycling on the form, we want to call a method called `_ToggleElevation()`.

As user submit the form by pressing the enter key, we want to create a new Running Object (Instance) or new Cycling Object based on the data that is coming in from the form. And as the user keeps adding Running or Cycling workout, a new object will be created for r=each of the workout and each of them will be stored in a Workouts Array which will hold all of these objects. And the method for this functionality is `_newWorkout()`.
![](Mapty-architecture-final.png) 

*Please note that will explain the remaining method as i start to explain the process!!!*
