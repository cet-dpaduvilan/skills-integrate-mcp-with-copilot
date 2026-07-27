# Mergington High School Activities API

A super simple FastAPI application that allows students to view and sign up for extracurricular activities.

## Features

- View all available extracurricular activities
- Teachers can sign up and unregister students (login required)
- Students can still view all participants

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

## API Endpoints

| Method | Endpoint                                                          | Description                                                         |
| ------ | ----------------------------------------------------------------- | ------------------------------------------------------------------- |
| GET    | `/activities`                                                     | Get all activities with their details and current participant count |
| POST   | `/activities/{activity_name}/signup?email=student@mergington.edu` | Sign up a student for an activity (teacher login required)          |
| DELETE | `/activities/{activity_name}/unregister?email=student@...`       | Unregister a student from an activity (teacher login required)      |
| POST   | `/auth/login`                                                     | Teacher login (JSON body: `username`, `password`)                  |
| POST   | `/auth/logout`                                                    | Teacher logout                                                      |
| GET    | `/auth/me`                                                        | Get current authentication status                                  |

## Teacher Credentials

Teacher credentials are stored in `teachers.json` and checked by the backend.

Default examples:

- `teacher1` / `welcome123`
- `coach` / `soccer2026`

## Data Model

The application uses a simple data model with meaningful identifiers:

1. **Activities** - Uses activity name as identifier:

   - Description
   - Schedule
   - Maximum number of participants allowed
   - List of student emails who are signed up

2. **Students** - Uses email as identifier:
   - Name
   - Grade level

All data is stored in memory, which means data will be reset when the server restarts.
