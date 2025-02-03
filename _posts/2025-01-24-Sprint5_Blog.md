---
title: Sprint 5 Blog
layout: post
description: Sprint 5 Blog
permalink: /Sprint5_Blog
toc: true
comments: true
---

Group Purpose: The purpose of our group’s program is to create a multiplayer drawing and guessing game inspired by Scribble.io. This program allows players to take turns drawing while others guess the word or phrase being illustrated. The goal is to provide an entertaining and interactive way for people to engage in creative gameplay, fostering collaboration, quick thinking, and creativity.

Individual Feature: Timer management and saving/loading drawings.


## 1. List Requests, Use of Lists, Dictionaries, and Database
## List Requests
## The Stats API supports the following requests:


*GET /api/competition: Retrieve timer status
POST /api/competition: Add's data: name, timer, drawings_drawn
PUT /api/competition: Update existing competition data
DELETE /api/competition/<user_name>/<Guess>: Delete a specific stat entry.


## Use of Lists and Dictionaries
We use lists to handle multiple competition entries such as timer and drawing data, and dictionaries for individual data. These dictionaries are converted for a JSON response.


## Example:
times = Time.query.all()
return jsonify([time.read() for time in times]), 200


data = request.json
new_time = Time(
 users_name=data.get('users_name'),
 timer=data.get('timer'),
 amount_drawn=data.get('amount_drawn')
)
db.session




2. Formatting Response Data (JSON) from API into DOM
We use Flask’s jsonify function to format the response data as JSON. In the frontend, we use JavaScript to fetch the JSON data from the API and update the DOM. This involves converting the JSON response into HTML elements to display the statistics.


## Example:
@competitors_api.route('/api/timer_status', methods=['GET'])
def timer_status():
   """API endpoint to get the current timer status."""
   return jsonify(timer_state)


3. Database Queries
We use SQLAlchemy ORM to interact with the database. SQLAlchemy provides methods to query the database and return results as Python lists. Foor instance, I can pull the


Example:
time_entry.users_name = data.get('users_name', time_entry.users_name)
time_entry.timer = data.get('timer', time_entry.timer)
time_entry.amount_drawn = data.get('amount_drawn', time_entry.amount_drawn)


4. CRUD Methods in Class
We define methods in the StatsEntry class to perform CRUD operations on the database:


Create: Adds a new entry to the database.
Read: Converts a database entry to a dictionary.
Update: Updates entry fields with new data.
Delete: Removes an entry from the database.


## Example:
class Time(db.Model):
   __tablename__ = 'timer_data_table'


   id = db.Column(db.Integer, primary_key=True)
   users_name = db.Column(db.String(255), nullable=False)
   timer = db.Column(db.String(255), nullable=False)
   amount_drawn = db.Column(db.Integer, nullable=False)


   def __init__(self, users_name, timer, amount_drawn):
       self.users_name = users_name
       self.timer = timer
       self.amount_drawn = amount_drawn


   def create(self):
       try:
           db.session.add(self)
           db.session.commit()
           print(f"Time Added: {self.users_name} - Timer: '{self.timer}' - Amount Drawn: {self.amount_drawn}")
       except IntegrityError:
           db.session.rollback()
           return None
       return self


   def read(self):
       return {
         "id": self.id,
           "users_name": self.users_name,
           "timer": self.timer,
           "amount_drawn": self.amount_drawn
       }


   def delete(self):
       db.session.delete(self)
       db.session.commit()


5. Algorithmic Code Request
We define API endpoints to handle different types of requests. For example, the PUT request to update a statistics entry involves checking if the entry exists, updating the score if it does, or creating a new entry if it doesn’t.


Example:
@competitors_api.route('/api/times/<int:time_id>', methods=['PUT'])
def modify_time(time_id):
   time_entry = Time.query.get(time_id)
   if not time_entry:
       return jsonify({"error": "Time entry not found"}), 404
  
   if request.method == 'PUT':
       data = request.json
       time_entry.users_name = data.get('users_name', time_entry.users_name)
       time_entry.timer = data.get('timer', time_entry.timer)
       time_entry.amount_drawn = data.get('amount_drawn', time_entry.amount_drawn)
       db.session.commit()
       return jsonify({"message": "Time entry updated successfully"})


6. API Class
We use Flask’s Blueprint to define the API routes. The stats_api blueprint handles the GET, POST, PUT, and DELETE methods, allowing us to organize the API endpoints and their implementations.


## Example:
competition_api = Blueprint('competition_api', __name__)


@competition_api.route('/api/competition', methods=['GET'])
def timer_status():
   # Implementation


@competition_api.route('/api/competition', methods=['POST'])
def start_timer():
   # Implementation


@competition_api.route('/api/competition', methods=['PUT'])
def modify_time():
   # Implementation


@competition_api.route('/api/competition/<profile_name>/<game_name>', methods=['DELETE'])
def modify_time(name, timer, drawings_drawn):
   # Implementation


7. Method with Sequencing, Selection, and Iteration
The modify_time  method contains sequencing (steps to process the request), selection (conditional checks), and iteration (looping through data if needed). This updates a current entry, or deletes and recreates a new one.


## Example:
@competitors_api.route('/api/times/<int:time_id>', methods=['PUT', 'DELETE'])
def modify_time(time_id):
   time_entry = Time.query.get(time_id)
   if not time_entry:
       return jsonify({"error": "Time entry not found"}), 404
  
   if request.method == 'PUT':
       data = request.json
       time_entry.users_name = data.get('users_name', time_entry.users_name)
       time_entry.timer = data.get('timer', time_entry.timer)
       time_entry.amount_drawn = data.get('amount_drawn', time_entry.amount_drawn)
       db.session.commit()
       return jsonify({"message": "Time entry updated successfully"})


8. Parameters and Return Type
The modify_time method takes JSON data as input and returns a JSON response. The input data includes name, timer, and amount_drawn. The response is formatted using jsonify to ensure it is returned as a JSON object.


## Example:
@competitors_api.route('/api/times/<int:time_id>', methods=['PUT', 'DELETE'])
def modify_time(time_id):
   time_entry = Time.query.get(time_id)
   if not time_entry:
       return jsonify({"error": "Time entry not found"}), 404
  
   if request.method == 'PUT':
       data = request.json
       time_entry.users_name = data.get('users_name', time_entry.users_name)
       time_entry.timer = data.get('timer', time_entry.timer)
       time_entry.amount_drawn = data.get('amount_drawn', time_entry.amount_drawn)
       db.session.commit()
       return jsonify({"message": "Time entry updated successfully"})
  
   if request.method == 'DELETE':
       db.session.delete(time_entry)
       db.session.commit()
       return jsonify({"message": "Time entry deleted successfully"})
       
9. Call to Algorithm Request
On Frontend, we fetch the API to make requests to the backend. For example, to submit a score, we send a PUT request to the user_name, timer data, and amount_drawn. The response is handled by checking each instance of the data and updating the DOM accordingly. If the request is successful, we update the timer, amount_drawn, and user data; If not, it proceeds an error message.



