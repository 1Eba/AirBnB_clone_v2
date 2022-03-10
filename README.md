HBNB - The Console
This repository contains the initial stage of a student project to build a clone of the AirBnB website. This stage implements a backend interface, or console, to manage program data. Console commands allow the user to create, update, and destroy objects, as well as manage file storage. Using a system of JSON serialization/deserialization, storage is persistent between sessions.

Table of Contents
Description
File Structure
Requirements
Quick Start
Usage
Bugs
Authors
Description
The Console

Will help us to:

Create your data model
Manage (create, update, destroy, etc) objects via a console / command interpreter
Store and persist objects to a file (JSON file)
In this case, we want to be able to manage the objects of our project:

Create a new object (ex: a new User or a new Place)
Retrieve an object from a file, a database etc…
Do operations on objects (count, compute stats, etc…)
Update attributes of an object
Destroy an object
File Structure
These are the files with the custom funtions and system calls, each one contains a brief description:

File	Description
console.py	Console file
models	Contains all the classes
models/__init__	Connects with filestorage
models/base_model	Base Model class
models/user	User class
models/state	State class
models/city	City class
models/place	Place class
models/amenity	Amenity class
models/review	Review class
models/engine	Contains File Storage engine
models/engine/file_storage	File Storage module
models/engine/db_storage	MySQL Storage module
tests	Prompt and getline file
AUTHORS	AUTHORS file
README.md	README.md file
Requirements
All files will be interpreted/compiled on Ubuntu 14.04 LTS using python3
Code should use the PEP 8 style (version 1.7 or more)
Your code should use the PEP 8 style (version 1.7 or more)
Usage
Interactive Mode JSON file engine storage:
Supported classes:
BaseModel
User
State
City
Amenity
Place
Review
Commands:
create - create an object
show - show an object (based on id)
destroy - destroy an object
all - show all objects, of one type or all types
quit/EOF - quit the console
help - see descriptions of commands
To start, navigate to the project folder and enter ./console.py in the shell.

Create
create <class name> Ex: create BaseModel

Show
show <class name> <object id> Ex: show User my_id

Destroy
destroy <class name> <object id> Ex: destroy Place my_place_id

All
all or all <class name> Ex: all or all State


Examples
Primary Command Syntax
Example 0: Create an object
Usage: create <class_name>

(hbnb) create BaseModel
(hbnb) create BaseModel
3aa5babc-efb6-4041-bfe9-3cc9727588f8
(hbnb)                   
Example 1: Show an object
Usage: show <class_name> <_id>

(hbnb) show BaseModel 3aa5babc-efb6-4041-bfe9-3cc9727588f8
[BaseModel] (3aa5babc-efb6-4041-bfe9-3cc9727588f8) {'id': '3aa5babc-efb6-4041-bfe9-3cc9727588f8', 'created_at': datetime.datetime(2020, 2, 18, 14, 21, 12, 96959), 
'updated_at': datetime.datetime(2020, 2, 18, 14, 21, 12, 96971)}
(hbnb)  
Example 2: Destroy an object
Usage: destroy <class_name> <_id>

(hbnb) destroy BaseModel 3aa5babc-efb6-4041-bfe9-3cc9727588f8
(hbnb) show BaseModel 3aa5babc-efb6-4041-bfe9-3cc9727588f8
** no instance found **
(hbnb)   
Example 3: Update an object
Usage: update <class_name> <_id>

(hbnb) update BaseModel b405fc64-9724-498f-b405-e4071c3d857f first_name "person"
(hbnb) show BaseModel b405fc64-9724-498f-b405-e4071c3d857f
[BaseModel] (b405fc64-9724-498f-b405-e4071c3d857f) {'id': 'b405fc64-9724-498f-b405-e4071c3d857f', 'created_at': datetime.datetime(2020, 2, 18, 14, 33, 45, 729889), 
'updated_at': datetime.datetime(2020, 2, 18, 14, 33, 45, 729907), 'first_name': 'person'}
(hbnb)
Alternative Syntax
Example 0: Show all User objects
Usage: <class_name>.all()

(hbnb) User.all()
["[User] (99f45908-1d17-46d1-9dd2-b7571128115b) {'updated_at': datetime.datetime(2020, 2, 19, 21, 47, 34, 92071), 'id': '99f45908-1d17-46d1-9dd2-b7571128115b', 'created_at': datetime.datetime(2020, 2, 19, 21, 47, 34, 92056)}", "[User] (98bea5de-9cb0-4d78-8a9d-c4de03521c30) {'updated_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134362), 'id': '98bea5de-9cb0-4d78-8a9d-c4de03521c30', 'created_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134343)}"]
Example 1: Destroy a User
Usage: <class_name>.destroy(<_id>)

(hbnb) User.destroy("99f45908-1d17-46d1-9dd2-b7571128115b")
(hbnb)
(hbnb) User.all()
(hbnb) ["[User] (98bea5de-9cb0-4d78-8a9d-c4de03521c30) {'updated_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134362), 'id': '98bea5de-9cb0-4d78-8a9d-c4de03521c30', 'created_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134343)}"]
Example 2: Update User (by attribute)
Usage: <class_name>.update(<_id>, <attribute_name>, <attribute_value>)

(hbnb) User.update("98bea5de-9cb0-4d78-8a9d-c4de03521c30", name "Todd the Toad")
(hbnb)
(hbnb) User.all()
(hbnb) ["[User] (98bea5de-9cb0-4d78-8a9d-c4de03521c30) {'updated_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134362), 'id': '98bea5de-9cb0-4d78-8a9d-c4de03521c30', 'name': 'Todd the Toad', 'created_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134343)}"]
Example 3: Update User (by dictionary)
Usage: <class_name>.update(<_id>, )

(hbnb) User.update("98bea5de-9cb0-4d78-8a9d-c4de03521c30", {'name': 'Fred the Frog', 'age': 9})
(hbnb)
(hbnb) User.all()
(hbnb) ["[User] (98bea5de-9cb0-4d78-8a9d-c4de03521c30) {'updated_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134362), 'name': 'Fred the Frog', 'age': 9, 'id': '98bea5de-9cb0-4d78-8a9d-c4de03521c30', 'created_at': datetime.datetime(2020, 2, 19, 21, 47, 29, 134343)}"]

Authors
Eba Mengistu Baisa - 1Eba
