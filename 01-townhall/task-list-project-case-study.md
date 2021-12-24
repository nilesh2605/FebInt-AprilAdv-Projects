# Project - Build a Task Manager

## Features
	- Multiple users can use the app 
	- Every user can add tasks 
	- After creating a task, user can assign it to different user 
	- Tasks
		- has a description
		- priority: enum<high/low/medium>
		- has a due date
		- has a state: pending / completed 
		- Notes
			- A task can have multiple notes inside it
			- Notes can be made by the owner or asignee 
	- The creator of the task can edit / delete the task 
	- The creator or asignee can mark the task as done 


## DB Schema Design

base_table
- id  - 			integer autoincrement primary key
- created_at - 	date
- updated_at -	date
	

users
- name - string(100)
- email - string(100) : validate(email)

tasks
- description - string
- priority - enum[high,medium,low]
- due_date - date
- status   - enum[pending,completed]
- creator_id  - fk(users.id)
- asignee_id	- fk(users.id)

notes 
- task_id		- fk(tasks.id)
- description - string 
- author_id	- fk(users.id)

## REST API

HINT: Complete this like https://github.com/scaleracademy/open-source-projects/discussions/81#discussioncomment-869800 



##auth
POST /auth/login
Login and get auth token

##users
GET /users
Get details of all users

GET /users/{userid}
Get details of given user by userid

POST /users
Create a new user

PATCH /users/{userid} 🔒
Update a user

PUT /users/{userid} 🔒
Update a user

DELETE /users/{userid} 🔒
Delete a user

##tasks
GET /users/{userid}/tasks
Get details of all the tasks for a given user

GET /users/{userid}/tasks/{taskid}
Get details of a particular task for a given user

POST /users/{userid}/tasks🔒
Create task

PATCH /users/{userid}/tasks/{taskid}🔒
Update task

PUT /users/{userid}/tasks/{taskid}🔒
Update task

DELETE /users/{userid}/tasks/{taskid}🔒
Update task

##notes
GET /users/{userid}/tasks/{taskid}/notes
Get details of all the notes for a given task of a user.

GET /users/{userid}/tasks/{taskid}/notes/{noteid}
Get details of a particular note for a given task of a user.

POST /users/{userid}/tasks/{taskid}/notes🔒
Create note

PATCH /users/{userid}/tasks/{taskid}/notes/{noteid}🔒
Update note.

PUT /users/{userid}/tasks/{taskid}/notes/{noteid}🔒
Update note.

DELETE /users/{userid}/tasks/{taskid}/notes/{noteid}🔒
Delete note.
