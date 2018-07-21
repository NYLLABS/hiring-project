
Welcome, candidate! Thank you for your interest in our application process. Please read this document carefully, it will provide everything you need for completing the next phase of your application process.

We recognize the time it takes to complete a take-home project, therefore all projects will recieve an assessment of their work, including both areas of achievement and areas for improvment, regardless of next steps in their candidacy.

The project can be finished in as little as 2 days. We expect the project to take no more than 4 days.

# Intro

Robo Inc., an innovative tech giant in Silicon Alley (Yes, "Alley"--they're based in NYC of course!) has developed fully functional robotic assistants, know as **robo-assistants** (Think _iRobot_ without the curfew or revolutions). They are working on a website for customers to use. They can search for robo-assistants and view details on them. They need to build an interface that can be used to lookup these assistants. Luckily, you're a developer that can help with these plans!

# On using a framework

This project is written with an Angular (2) scaffold. You are welcome to choose a different framework (such as React or Vue) if you are more experienced. 

# Prerequisites.

+ node `6+` environment.
+ Angular cli (if using this projects scaffold)
  + `npm install -g @angular/cli`
+ Docker (for the development API)

# Setting up the project the project.

If using your own framework, skip this step. We recommend using a well-supported generator in the framework of your choice.

+ Fork the repository
+ `npm install`
+ `ng serve`
+ To build a `dist`, run `ng build`

# Requirements

A successful completion of this project involves:

- [ ] Search functionality on the app (users can search for a robo-assistast by name)
- [ ] Detail pages for specific robo-assistant (with full reviews)

For extra credit, especially if you are interested on a front-end focused role:

- [ ] Add styling to the app. Unless you are interested in a UX engineering role, the actual design will not be critiqued, just how well the css itself is implemented.
- [ ] Any other functionality you would like. Eg infinite scrolling, star svgs for ratings, etc. If there's something you specialize in and can quickly add, the project is free-range!

# Your tickets (Do these!)

Below are the "tickets" to help you complete all aspects of the project in the most efficient order. They are broken up into **Backend Suggestions** and **Frontend Needs**. We recommend working back to front.

## Backend Suggestions.

> NOTE: You don't need to do all this backend stuff, but it will surely help you stay organized and understand what is going on for building the front end app ;)


### B1. Understand the Data models.

Checkout the [data models](https://github.com/NYLLABS/hiring-robo-project/wiki/Data-Models), you will be the working very closely with this data.

The trickiest part is that the reviews for each robo-assistant is not embedded in the document. Think about ways to fetch the reviews when you need them for a corresponding robo-assistant.


### B2. Understand the API

[Robo-assist API](https://github.com/NYLLABS/hiring-project/wiki/Robo-assist-API) is the premiere API for accessing the robo-assistant database. It will be helpful to verify that you can make calls to all the routes.

+ Use [Postman](https://www.getpostman.com/), cURL, or [httpie](https://httpie.org/) for testing the routes.
+ Follow the documentation to:
    + get an authorization token
    + configure the authorization token.
+ Test that other routes are accessible.

## Frontend Needs

> NOTE: These tickets specifically point out files in the Angular scaffold. If using a different framework, these will obviously be irrelivant. Do keep files/components/whatnot organized in a similar manner.

### F1. Use `roboAssistant.service.ts` to incorporate API calls

The robo-assistant service uses Angular's [http](https://angular.io/docs/ts/latest/tutorial/toh-pt6.html) [service](https://angular.io/docs/ts/latest/api/http/index/Http-class.html) to make calls. You will need to:

+ Set the [headers](https://angular.io/docs/ts/latest/api/http/index/Headers-class.html) to use your authorization token. (You may set headers any way you like, but Angulars Headers class might be least error-prone)
+ Add the API urls to the provided method, and add your own methods for the other api.
+ When you need to make different API calls, you can add other methods here as needed.

### F2. Add Search bar to `search.component.ts`, and incorporate `roboAssistantService`

+ Add a search bar with [two-way data binding](https://angular.io/docs/ts/latest/guide/architecture.html#!#sts=Data%20binding) for the user to search for Robo-assistants.
+ Add a click event to a search button, which will populate the view with a list of matching robo-assistants from the API. Each entry should have a hyperlink, changing the route to `/detail/:robo_id`, where `:robo_id` is the `robo_id` of the robo-assistant.
+ Each robo-assistant rendered should include the following information
    + name
    + model
    + rating
    + price **(In USD format (no cents), eg `$1,482,483`)**

### F3. Complete missing parts of `detail.component.ts`
In `src/app/detail/detail.component.ts`, complete the options object in the decorator to include `detail.component.html` as the template, and `detail.component.css` as the style.

### F4. Add `DetailComponent` to the routing in `app.module.ts`

`DetailComponent` is exported in `src/app/detail/detail.component.ts`, but not yet included in the router. So we have no access to it!

+ Add a route `/detail/:robo_id` to `app.module.ts`, using the `DetailComponent` for loading.

### F5. Configure detail page to fetch and display a robo-assistast.

+ Make sure the `RoboAssistantsService` has a method to get an individual robo-assistant. And their reviews.
+ Fetch the correct robo-assistant from the url param `:robo_id`
+ Ensure corresponding reviews are also fetched
+ Display all info on the html page.



## Submitting

You should zip the project and submit it as an attachment to the R&D Lab representitive who contacted you. Thank you again for your interest!
