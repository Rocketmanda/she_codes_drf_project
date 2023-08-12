# DRF Crowdfunding Project
By Amanda Hagaman
She Codes Crowdfunding Project - DRF Backend.


## About
The purpose of this website is to provide a platform for users to crowdsource for their dogs' boujee lifestyle. Users can create a Project and/or submit a pledge to fund someone's activities for their dog, such as a Doggy Daycare session or a Pooch Pedicure.

## Features
The features of the MVP for this project include:
* [X] Ability for a user to create a project
* [X] Ability for a user to make a pledge
* [X] Ability for a user to log in and out
* [X] Ability to create a new user.

### Stretch Goals
The following features are stretch goals following MVP:

* [ ] Display total projects and pledges in real-time on the home page
* [ ] Ability for a Supporter to edit an existing pledge
* [ ] Ability for a User to edit an existing Project

## API Specification

| HTTP Method | Url | Purpose | Request Body | Successful Response Code | Authentication <br /> Authorization
| --- | ------- | ------ | ---- | -----| ----|
| GET | /projects/ | Return all projects | N/A | 200 | N/A |
| POST | /projects/ | Create a new project | project object | 201 | User must be logged in.
| POST | /pledges/ | Create a new pledge | pledge object | 201 | Must be logged in.
| POST | /users/ | Create new user | user object | 200 | N/A

## Database Schema
![Project database schema](screenshots/Database%20Schema.png)

## Submission Documentation

Deployed Project: [Deployed website](https://small-firefly-695.fly.dev/projects/)

### How To Run
1. Clone the repo to your local machine - Navigate to the directory of your choice and run the following command:
-  `git clone https://github.com/Rocketmanda/she_codes_drf_project.git`
  
2. Set up Virtual Environment:

  - In your terminal, navigate to the folder containing requirements.txt file:
     - Mac run the following command: `source venv/bin/activate`
     - Windows run the following command: `venv/Scripts/activate`
  
 3. Install Django, Migrate, Load Data and Run:
  - `python3 -m pip install -r requirements.txt`
  - `python3 -m pip freeze` to check if install successful
  - `cd she_codes_drf_project/crowdfunding` to navigate to where manage.py file is contained
  - `python3 manage.py migrate` to make migrations
  - `python3 manage.py runserver` to run the server
  
#### Remember...
- Press CTRL+C to quit the server
- Enter the command `deactivate` in terminal to deacticate the virtual environment.

### How To Register a New User
1. Open Insomnia and make sure you are connected to the server API
2. Choose the HTTP method "POST" and enter the URL to the registration endpoint: `https://small-firefly-695.fly.dev/users/`
3. In the request body, enter the following JSON data to create a new user:
   
   `{
    "username": "new_user",
    "email": "new_user@example.com",
    "password": "your_password"
    }`

        Replace `"new_user"` with your desired username, `"new_user@example.com"` with your desired email address, and `"your_password"` with your desired password

4. Click the "Send" button to make the request
   
5. If successful, you should receive a response with status code 201 Created, and the JSON data containing the registered user's information.

### How To Create a New Project
1. Choose the HTTP method "POST" and enter the URL to your project creation endpoint: `https://small-firefly-695.fly.dev/projects/`
   
2. In the request body, enter the following JSON data to create a new project:
   
`{
    "id": 1,
    "title": "New Project",
    "description": "Description of new project.",
    "goal": 300,
    "image": "https://via.placeholder.com/300.jpg",
    "is_open": true,
    "date_created": "2020-03-20T14:28:23.382748Z",
    "owner": "Owner Description"
}`

    Replace the title, description, goal, image, and "1" with the user's primary key who will be the owner of the project (you can use the primary key of the user you registered earlier)

3. In the request headers, add an "Authorization" header with the value "Token your_token", where `"your_token"` is the token you received when registering the user
   
4. Click the "Send" button to make the request
5. If successful, you should receive a response with status code 201 Created and the JSON data containing the created project's information.

    Note: Make sure you have the necessary authentication and permissions set up in your Django REST Framework views to allow user registration and project creation.
    
### Screenshots
* [X] A screenshot of Insomnia, demonstrating a successful GET method for any endpoint.
![Screenshot of Get New Project in Insomnia](screenshots/GET%20Get%20New%20Project%20-%20Fly.io.png)

* [X] A screenshot of Insomnia, demonstrating a successful POST method for any endpoint.
![Screenshot of Create New User in Insomnia](screenshots/POST%20Create%20New%20User%20-%20Fly.io.png)

* [X] A screenshot of Insomnia, demonstrating a token being returned.
![Screenshot of Get Auth Token in Insomnia](screenshots/POST%20Get%20Auth%20Token%20-%20Fly.io.png)

