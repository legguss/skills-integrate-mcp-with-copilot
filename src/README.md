# Mergington High School Activities API

A super simple FastAPI application that allows students to view and sign up for extracurricular activities.

## Features

- View all available extracurricular activities
- Teacher login for managing activity registrations
- Sign up students for activities
- Remove students from activities

## Getting Started

1. Install the dependencies:

   ```
   pip install fastapi uvicorn
   ```

2. Run the application:

   ```
   python app.py
   ```

3. Open your browser and go to:
   - API documentation: http://localhost:8000/docs
   - Alternative documentation: http://localhost:8000/redoc

4. Use one of the demo teacher accounts when you need to manage registrations:

   ```
   msmith / mergington-math
   jcarter / debate-coach
   aprince / art-studio
   ```

## API Endpoints

| Method | Endpoint                                                          | Description                                                         |
| ------ | ----------------------------------------------------------------- | ------------------------------------------------------------------- |
| GET    | `/activities`                                                     | Get all activities with their details and current participant count |
| POST   | `/auth/login`                                                     | Log in as a teacher and get a session token                         |
| POST   | `/auth/logout`                                                    | Log out the current teacher session                                 |
| POST   | `/activities/{activity_name}/signup?email=student@mergington.edu` | Register a student for an activity as a teacher                     |
| DELETE | `/activities/{activity_name}/unregister?email=student@mergington.edu` | Remove a student from an activity as a teacher                  |

## Data Model

The application uses a simple data model with meaningful identifiers:

1. **Activities** - Uses activity name as identifier:

   - Description
   - Schedule
   - Maximum number of participants allowed
   - List of student emails who are signed up

2. **Teachers** - Uses usernames and passwords stored in `teachers.json`:

   - Username
   - Password

3. **Students** - Uses email as identifier:
   - Name
   - Grade level

All data is stored in memory, which means data will be reset when the server restarts.
