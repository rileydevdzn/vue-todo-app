# To-Do App with Vue, Vite and SASS

<div align="center">
  <picture>
    <source media="(max-width: 1199px)" srcset=".png"/>
    <source media="(min-width: 1200px)" srcset=".png"/>
    <img 
    src=""
    alt="To-Do app built with Vue.js, Vite and SASS"
    height="350px"
    max-width="100%"/>
  </picture>
  <p>To-Do App<!--</br><em><small>(if viewing on desktop, resize the browser window to see the mobile version)</small></em>--></p>
</div>

</br>

## Table of contents

- [Overview](#overview)
  - [Links](#links)  
  - [Highlights](#highlights)
- [Build details](#build-details)
  - [Features](#features)
  - [Challenges](#challenges)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
  - [Useful resources](#useful-resources)
- [Author](#author)

</br>

## Overview

For this project, I created a fully functional to-do app using Vue, Vite and SASS. I focused on creating a simple and intuitive UI that allows users to dynamically add, filter, edit, and delete tasks while tracking their progress with visuals.

My build needed to fulfill the following:

- provide functionality to view a list of to-dos, update completion status, add new tasks, and edit or delete existing tasks 
- track completion progress with multiple visuals available at a glance
- filter tasks by completion status
- mobile-first design

</br>

### Links

View live page: [Vue.js To-Do App]()

</br>

### Highlights

- View list of to-dos and mark tasks as completed
  - [View to-do list and mark tasks as completed](#view-to-do-list-and-mark-tasks-as-completed)
- Add new tasks and update task list
  - [Add new tasks](#add-new-tasks)
- Edit or delete existing tasks and update task list
  - [Edit and delete tasks](#edit-or-delete-tasks)
- Filter tasks by completion status
  - [Filter tasks](#filter-tasks)

</br>

</br>

## Build details

### Features

#### *View to-do list and mark tasks as completed*



</br>

<div align="center">
  <img
    src=".gif"
    alt="Video demo of marking tasks completed in to-do app"
    width="285px">
  <p><em>Marking tasks as completed with visual feedback</em></p>
</div>

</br>

#### *Add new tasks*

<div align="center">
  <img
    src=".gif"
    alt="Video demo of adding new tasks to to-do list"
    width="285px">
  <p><em>Adding new tasks to the to-do list</em></p>
</div>


</br>

#### *Edit or delete tasks*





</br>


#### *Filter tasks*

<div align="center">
  <img
    src=".gif"
    alt="Video demo of filtering the to-do list"
    width="100%">
  <p><em>Filtering to-dos by completion status</em></p>
</div>


### Challenges

The most challenging part of this project was ensuring the proper flow of props and emitting events between components. I used various levels of nesting with multiple components, thinking not just of how I wanted to organize the component tree for this first iteration, but also keeping in mind how I want to organize and display components across different views in a future build when I create the single-page application (SPA) version.

I also created a number of side-challenges along the way for myself. I added cancel buttons to both the add and edit functions, for example, to make it easy for a user to back out of actions. Small details, like consistent organization and styling of actions and buttons, adding multiple visual indicators for feedback, and auto-closing the add/edit forms upon completion were important to make the interactions feel smooth and intuitive for the user.

The dynamically updating visual progress bar was the part of the build I was most excited to solve. I used computed properties to calculate the (decimal) portion of tasks completed versus total tasks, converted this number to a percentage format then used binding to dynamically update the width of the progress bar as the task list was updated.

</br>

### What I learned

#### *Vue events, methods, models and binding*



#### *Vue computed properties and conditional rendering*



#### *Global and component styling with SASS*


</br>

### Continued development

In this first iteration, I focused on the fundamentals of the user experience: 
- what functions does a to-do app need to perform to be useful?
- how to design a UI that makes accomplishing these functions feel intuitive and easy to complete? 

The result was a simple app that fulfills all of the primary actions a user needs from a to-do app and does them well.

In the next iteration I plan to incorporate additional design elements (like a confirmation modal for deleting tasks) and development work, adding Vue Router for a single-page application (SPA) and state management with Pinia.

</br>

### Useful resources

- [Vue.js Guide](https://vuejs.org/guide/introduction.html) - Official docs for Vue.js, very helpful for diving into specific topics like props and v-model.
- [Vue.js Examples](https://vuejsexamples.com/) - A collection of apps, sites, clones and plugins created using Vue.js. I found this very useful to see builds and use cases with various tools and seeing different ways others approach a problem gave me ideas to test and refine my own solutions.

</br>

## Author

- Riley - [View Portfolio](https://rileydevdzn.webflow.io)
