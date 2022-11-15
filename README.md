# Password Protection Lab

## Learning Goals

- Implement login and signup with a password.
- Use `Bcrypt` to salt and hash passwords.

***

## Key Vocab

- **Identity and Access Management (IAM)**: a subfield of software engineering that
  focuses on users, their attributes, their login information, and the resources
  that they are allowed to access.
- **Authentication**: proving one's identity to an application in order to
  access protected information; logging in.
- **Authorization**: allowing or disallowing access to resources based on a
  user's attributes.
- **Session**: the time between a user logging in and logging out of a web
  application.
- **Cookie**: data from a web application that is stored by the browser. The
  application can retrieve this data during subsequent sessions.

***

## Introduction

We're going to make a Flask app that covers a simple authentication flow: users
can create accounts, log in, and log out.

There is some starter code in place for a Flask API backend and a React frontend.
To get set up, run:

```console
$ pipenv install && pipenv shell
$ npm install --prefix client
$ cd server
$ flask db upgrade
$ python seed.py
```

You can work on this lab by running the tests with `pytest -x`. It will also be
helpful to see what's happening during the request/response cycle by running the
app in the browser. You can run the Flask server with:

```console
$ flask app.py
```

And you can run React in another terminal with:

```console
$ npm start --prefix client
```

You don't have to make any changes to the React code to get this lab working.

***

## Setup

Our app has three pages:

1. A signup page, where the user enters their username, password, and password
   confirmation.
2. A login page, where the user submits their username and password and are then
   logged in.
3. A user homepage, which says, "Welcome, ${username}!"

Users should not be able to log in if they enter an incorrect password.

> **Note: we're not covering password validations in this lab, so don't worry
> about those. Password validation is hard to get right anyway — it's
> surprisingly easy to produce rules that decrease password security rather than
> enhance it.**

***

## Instructions

To complete the lab and get the tests passing, you will need to:

- Create a `Signup` resource with a `post()` method that responds to a
  `POST /signup` request. It should: create a new user; save their hashed
  password in the database; save the user's ID in the session object; and return
  the user object in the JSON response.

- Add a `get()` method to your `CheckSession` resource that responds to a
  `GET /check_session` request. If the user is authenticated, return the user
  object in the JSON response. Otherwise, return an empty response with a 204
  status code.

- Create a `Login` resource with a `post()` method for logging in that
  responds to a `POST /login` request and returns the user as JSON.
  
- Create a `Logout` resource with a `delete()` method for logging out
  that responds to a `DELETE /logout` request.

Happy coding!

***

## Resources

- [Flask-Bcrypt][bcrypt]

[bcrypt]: https://flask-bcrypt.readthedocs.io/en/1.0.1/
