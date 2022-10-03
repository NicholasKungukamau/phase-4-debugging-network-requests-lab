# Putting it All Together: Client-Server Communication

## Learning Goals

- Understand how to communicate between client and server using fetch, and how
  the server will process the request based on the URL, HTTP verb, and request
  body
- Debug common problems that occur as part of the request-response cycle

## Introduction

Just like the last lesson, we've got code for a React frontend and Rails API
backend set up. This time though, it's up to you to use your debugging skills to
find and fix the errors!

To get the backend set up, run:

```console
$ bundle install
$ rails db:migrate db:seed
$ rails s
```

Then, in a new terminal, run the frontend:

```console
$ npm install --prefix client
$ npm start --prefix client
```

Confirm both applications are up and running by visiting
[`localhost:4000`](http://localhost:4000) and viewing the list of toys in your
React application.

## Deliverables

In this application, we have the following features:

- Display a list of all the toys
- Add a new toy when the toy form is submitted
- Update the number of likes for a toy
- Donate a toy to Goodwill (and delete it from our database)

The code is in place for all these features on our frontend, but there are some
problems with our API! We're able to display all the toys, but the other three
features are broken.

Use your debugging tools to find and fix these issues.

There are no tests for this lesson, so you'll need to do your debugging in the
browser and using the Rails server logs and `byebug`.

**Note**: You shouldn't need to modify any of the React code to get the
application working. You should only need to change the code for the Rails API.

As you work on debugging these issues, use the space in this README file to take
notes about your debugging process. Being a strong debugger is all about
developing a process, and it's helpful to document your steps as part of
developing your own process.

## Your Notes Here

- Add a new toy when the toy form is submitted

  - How I debugged:

Opening Console Tab and seeing it has a 500 internal Server Error that means easiest way to solve this is by using Rails Server log. 
By checking on server log and following the instructions thrown by error to find where Name error was. Resolved by proper initialization of controller.

- Update the number of likes for a toy

  - How I debugged:

  From console tab found it is Uncaught (in promise) SyntaxError: Unexpected end of JSON input which mean you need to look at fetch request and controller action.
  Start by adding a byebug in update contoller action. Then, enter some data in the form, and submit the form again to make another request. Use this as an opportunity to inspect the request object, in particular looking at the params hash. Then return JSON data in the response from your controller actions.


- Donate a toy to Goodwill (and delete it from our database)

  - How I debugged:
  Using console tab and found it is a DELETE http://localhost:4000/toys/49 404 (Not Found) error. By looking in Server log error found out it was ActionController::RoutingError (No route matches [DELETE] "/toys/1"). This mean that there is no route to perform DELETE action.
  Added it in routes.rb(:destroy)



