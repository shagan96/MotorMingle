# MotorMingle

## Current Progress
We have implemented almost all the pages, except our browse events page. Our database is set up with tables for Users, Cars, Events, and tables for Instagram, Facebook, and Twitter. There is also an Attendees table which links the Events and Users tables. We also populated the database with some default data, like some example users and events. 

## What Is Not Done
- [ ] Fix db setup bugs to not keep failing during deployment
- [ ] Finish implementing User Profile client-side js
- [ ] Finish implementing Create Event html/css
- [ ] Finish implementing APIClient
- [ ] Add server-side validation for event creation
- [ ] Finish implementing reading in real data for My Cars page
- [ ] Figure out how to store images in db
- [ ] Squash bugs in Joined Event page
- [ ] System Testing
- [ ] Deploy to VM

## Page Status
Pages   | Status | Wireframe
------- | ------ | ---------
Landing   | ✅    | [Mobile wireframe](https://github.ncsu.edu/engr-csc342/csc342-2023Spring-groupN/blob/main/Proposal/wireframes/Mobile_Landing_Pages.png)
Sign In | ✅     | [Mobile wireframe](https://github.ncsu.edu/engr-csc342/csc342-2023Spring-groupN/blob/main/Proposal/wireframes/Mobile_SignIn_Page.png)
User Profile   | ✅     | [Desktop wireframe](https://github.ncsu.edu/engr-csc342/csc342-2023Spring-groupN/blob/main/Proposal/wireframes/PC_UserProfile_Page.png)
My Cars | ✅     | [Mobile wireframe](https://github.ncsu.edu/engr-csc342/csc342-2023Spring-groupN/blob/main/Proposal/wireframes/Mobile_Profile_Cars_Pages.png)
Add/Edit Cars   | ✅     | [Mobile wireframe](https://github.ncsu.edu/engr-csc342/csc342-2023Spring-groupN/blob/main/Proposal/wireframes/Mobile_Profile_Cars_Pages.png)
Browse Events  | 0%    | [Desktop wireframe](https://github.ncsu.edu/engr-csc342/csc342-2023Spring-groupN/blob/main/Proposal/wireframes/PC_Home_Page.png)
Create Events  | ✅    | [Mobile wireframe](https://github.ncsu.edu/engr-csc342/csc342-2023Spring-groupN/blob/main/Proposal/wireframes/Mobile_Created_Events_Page.png)
View Created Events  | ✅    | [Mobile wireframe](https://github.ncsu.edu/engr-csc342/csc342-2023Spring-groupN/blob/main/Proposal/wireframes/Mobile_Created_Events_Page.png)
View Joined Events  | ✅    | [Mobile wireframe](https://github.ncsu.edu/engr-csc342/csc342-2023Spring-groupN/blob/main/Proposal/wireframes/Mobile_Joined_Events_Page.png)

## API Endpoints
These are the endpoints we have planned for our project
Method | Route                 | Description
------ | --------------------- | ---------
`POST` | `/users`              | Creates a new user account and returns the user object
`POST` | `/users/:userId/login`           | Authenticates a user log in with the users id
`GET`  | `/users/:userId`      | Retrieves a user with the given user id
`PUT`  | `/users/:userId`      | Updates user information with the users id and returns the user object
`DELETE`  | `/users/:userId`      | Deletes a user's account and returns the user object
`GET`  | `/users/:userId/cars`      | Gets all the cars that a user owns
`POST`  | `/events`      | Creates a new event and returns the event object
`PUT`  | `/events/:eventId`      | Updates the details of an event by its event id and returns the event object
`GET`  | `/events`      | Gets all the available events
`GET`  | `/events/:eventId`      | Gets an event by its event id
`DELETE`  | `/events/:eventId`      | Deletes an event and returns the event object
`POST`  | `/events/:eventId/join`      | Joins an event with a given event id
`DELETE`  | `events/:eventId/leave`      | Leaves an event with a given event id
`GET`  | `/events/:eventId/users`      | Gets all the users attending an event with a given event id
`GET`  | `/event/:eventId/cars`      | Gets all the cars that will be at the event with the given event id
`POST`  | `/cars`      | Creates a new car and returns the car object
`PUT`  | `/cars/:carId`      | Updates a car with the given car id
`GET`  | `/cars/:carId`      | Gets a car with the given car id
`DELETE`  | `/cars/:carId`      | Delets a car with the given car id

## Authentication Process
We are using token-based authentication to identify and authenticate users of the application. Specifically, we are using JWTs as our token of choice. These tokens are generated when a user successfully logs in. A user is validated by matching their username with an entry in the table of users of the system. Then, the user's provided password is combined with their salt and hashed. Finally, the newly hashed password is compared to the hashed password stored in the user's entry in the table. If the hashes match, the user is successfully authenticated. The token has an expiry date that is used to manage the length of the user's session when they are logged in. If the token expires and the user attempts to carry out an authenticated action, they will be automatically logged out.

The user is authorized to carry out certain actions depending on if we pass in the TokenMiddleware to a certain endpoint.


## Database Schema
![schema](https://github.ncsu.edu/engr-csc342/csc342-2023Spring-groupN/blob/main/Milestone2/database/db_schema/schema.png)

## Team contributions
### Chai
- Worked on updating the myCars page and implementing the viewJoinedEvents page.
- Created database sql schema
- Worked on setting up the CarsDAO file with the appropriate endpoints


### Harshal
- Worked on updating User Profile page to make it send/return real data to the backend and database.
- Created APIClient to use for making client-side calls to the backend api.
- Created EventsDAO file
- Implementing Create Events page (html/css/js)

### Shagan
- Created View Created Events page (html/css/js)
- Updated Login and Landing pages
- Implemented user auth
- Debugged mysql bugs
