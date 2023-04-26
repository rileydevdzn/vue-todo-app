# To-Do App with Vue, Vite and SASS

<div align="center">
  <img
    src="./src/assets/Todo-app-overview.svg"
    alt="To-do app with list of items to complete, one task item marked completed and another left to do"
    width="285px">
  <p><em>Mobile-first To-Do App</em></p>
</div>

<!--<div align="center">
  <picture>
    <source media="(max-width: 1199px)" srcset=".png"/>
    <source media="(min-width: 1200px)" srcset=".png"/>
    <img 
    src=""
    alt="To-Do app built with Vue.js, Vite and SASS"
    height="350px"
    max-width="100%"/>
  </picture>
  <p>To-Do App</br><em><small>(if viewing on desktop, resize the browser window to see the mobile version)</small></em></p>
</div>-->

</br>

## Table of contents

- [Overview](#overview)
  <!--- [Links](#links)-->  
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

<!--### Links

View live page: [Vue.js To-Do App]()

</br>-->

### Highlights

- View list of to-dos and mark tasks as completed
  - [View to-do list and mark tasks as completed](#view-to-do-list-and-mark-tasks-as-completed)
- Add new tasks and update task list
  - [Add new tasks](#add-new-tasks)
- Edit or delete existing tasks and update task list
  - [Edit or delete tasks](#edit-tasks-and-update-task-list)
- Filter tasks by completion status
  - [Filter tasks](#filter-tasks)

</br>

</br>

## Build details

### Features

#### *View to-do list and mark tasks as completed*

The home view provides the user with dynamically updating progress trackers in the top header bar, including both numeric and visual indicators to provide a quick progress summary at a glance. 

Next I included filter buttons to allow users to view tasks by completion status (all, completed or active), followed by the list of to-dos with easily accessible buttons to add or edit tasks.

Marking a task as complete provides visual feedback on the task item itself, with a checkmark, strikethrough text and "grayed-out" effect to reduce its visual prominence in the list.

The progress trackers in the header also update whenever a task is added, deleted, or marked complete.

</br>

<div align="center">
  <img
    src="./src/assets/Todo-app-markcompleted.gif"
    alt="Video demo of marking tasks completed in to-do app"
    width="285px">
  <p><em>Marking tasks as completed with visual feedback and updated progress tracking</em></p>
</div>

</br>

#### *Add new tasks*

A large button with descriptive text allows users to add new tasks to the list. On click, the button is replaced with a form for the user to enter the name of the new task. 

Save and cancel buttons are included with contrasting visuals so the user can save the new task, or back out of the action with the cancel button. Saving the task adds it to the list and automatically updates the user's progress.

<div align="center">
  <img
    src="./src/assets/Todo-app-addtask.gif"
    alt="Video demo of adding new tasks to to-do list"
    width="285px">
  <p><em>Adding new tasks to the to-do list</em></p>
</div>

</br>

#### *Edit tasks and update task list*

To edit existing tasks, a user can click the edit button (along with icon) available on each task item. A new form opens and from here the user can update the task, save their changes, delete the task, or cancel.

Consistent layout and styling of buttons across the to-do list (buttons below), task items (button with icon at right), and forms (save and cancel) was intentional to make the app easy to learn and use. Icons were also included with the edit and delete buttons as secondary visual indicators for important actions.

<div align="center">
  <img
    src="./src/assets/Todo-app-edittask.gif"
    alt="Video demo of editing existing tasks in the to-do list"
    width="285px">
  <p><em>Editing tasks and updating the to-do list</em></p>
</div>

</br>

#### *Filter tasks*

A long list of to-dos can require a lot of scrolling, so I added filter buttons above the to-do list to allow the user to also view tasks by completion status and quickly see what's been accomplished and what tasks are still outstanding.

<div align="center">
  <img
    src="./src/assets/Todo-app-filterbtns.gif"
    alt="Video demo of filtering the to-do list"
    width="285px">
  <p><em>Filtering to-dos by completion status</em></p>
</div>

</br>

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

My solution was an app that is simple, easy to use, and pays attention to performing its primary purpose well. I'm using an iterative design process to incrementally implement new features, concentrating on functionality and ease-of-use (doing a few things and doing them well) over an extended feature list. 

In the next iteration I plan to incorporate additional design elements (like a confirmation modal for deleting tasks) and development work, adding Vue Router for a single-page application (SPA) version and eventually state management with Pinia as the app grows in size and complexity.

</br>

### Useful resources

- [Vue.js Guide](https://vuejs.org/guide/introduction.html) - Official docs for Vue.js, very helpful for diving into specific topics like props and v-model.
- [Vue.js Examples](https://vuejsexamples.com/) - A collection of apps, sites, clones and plugins created using Vue.js. I found this very useful to see builds and use cases with various tools and seeing different ways others approach a problem gave me ideas to test and refine my own solutions.

</br>

## Author

- Riley - [View Portfolio](https://rileydevdzn.webflow.io)
