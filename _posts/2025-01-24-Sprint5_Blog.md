---
title: Sprint 5 Blog
layout: post
description: Sprint 5 Blog
permalink: /Sprint5_Blog
toc: true
comments: true
---

### Purpose of the Program
- **Group Purpose**: The program, Scribble, manages a drawing competition with a timer, leaderboards, and guessing.
- **Individual Feature**: Timer management and saving/loading drawings.

### Input/Output Requests
- **Frontend API Request and Response**: 
  - **Start Timer**: `/api/start_timer` (POST)
    - **Request**: Starts a new timer with a specified duration.
    - **Response**: Returns a message indicating the timer has started and the duration.
    - **Example Request Body**: `{ "duration": 60 }`
    - **Example Response**: `{ "message": "Timer started", "duration": 60 }`
  - **Timer Status**: `/api/timer_status` (GET)
    - **Request**: Retrieves the current status of the timer.
    - **Response**: Returns the remaining time and whether the timer is active.
    - **Example Response**: `{ "time_remaining": 45, "is_active": true }`
  - **Save Drawing**: `/api/save_drawing` (POST)
    - **Request**: Saves a drawing sent as a Base64-encoded image.
    - **Response**: Returns a message indicating the drawing has been saved and the filename.
    - **Example Request Body**: `{ "canvasData": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA..." }`
    - **Example Response**: `{ "message": "Drawing saved on server", "filename": "drawing_1616161616.png" }`
  - **Get Drawings**: `/api/get_drawings` (GET)
    - **Request**: Fetches all saved drawings with details.
    - **Response**: Returns a list of saved drawings with filenames, paths, sizes, and last modified times.
    - **Example Response**: 
      ```json
      {
        "status": "success",
        "total_drawings": 2,
        "drawings": [
          {
            "filename": "drawing_1616161616.png",
            "path": "saved_drawings/drawing_1616161616.png",
            "size_in_bytes": 1024,
            "last_modified": "Wed, 24 Feb 2021 12:34:56 GMT"
          },
          {
            "filename": "drawing_1616161620.png",
            "path": "saved_drawings/drawing_1616161620.png",
            "size_in_bytes": 2048,
            "last_modified": "Wed, 24 Feb 2021 12:35:00 GMT"
          }
        ]
      }
      ```
  - **Get Times**: `/api/times` (GET)
    - **Request**: Retrieves all time entries from the database.
    - **Response**: Returns a list of time entries.
    - **Example Response**: 
      ```json
      [
        { "users_name": "Alice", "timer": 60, "amount_drawn": 5 },
        { "users_name": "Bob", "timer": 45, "amount_drawn": 3 }
      ]
      ```
  - **Add Time**: `/api/times` (POST)
    - **Request**: Adds a new time entry to the database.
    - **Response**: Returns a message indicating the time entry has been added successfully.
    - **Example Request Body**: `{ "users_name": "Alice", "timer": 60, "amount_drawn": 5 }`
    - **Example Response**: `{ "message": "Time entry added successfully" }`
- **Postman**: Demonstrate raw API requests and responses with error codes and JSON.
- **Database Operations**: Use `db_init`, `db_restore`, `db_backup` for data management.


### List Requests
- **Lists and Dictionaries**: 
  - Use lists to store drawings and timer states.
  - Use dictionaries to format JSON responses.
- **Formatting Response Data**: Convert Python data structures to JSON for API responses.
- **Database Queries**: Extract data using SQLAlchemy to get lists of times.
- **Class Methods**: CRUD operations for managing time entries in the database.


### Algorithmic Code Requests
- **API Class Methods**: 
  - GET, POST methods for timer and drawing management.
  - Methods include sequencing (steps to process requests), selection (error handling), and iteration (timer countdown).
- **Parameters and Return Types**: 
  - Parameters: JSON body for POST requests.
  - Return Type: JSON responses using `jsonify`.


### Call to Algorithm Requests
- **API Calls**: 
  - Fetch requests to API endpoints.
  - Handle responses by updating the DOM or logging errors.
- **Response Handling**: 
  - Different responses based on normal and error conditions.
  - Example: Validating duration for the timer and handling invalid input.
  

This list summarizes how the API meets the requirements by providing endpoints for managing a drawing competition, handling input/output requests, working with lists and dictionaries, and implementing algorithmic code.