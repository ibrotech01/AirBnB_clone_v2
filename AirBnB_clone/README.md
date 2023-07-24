HBNB - The Console
This repository contains the initial stage of a student project to build a clone of the AirBnB website. This stage implements a backend interface, or console, to manage program data. Console commands allow the user to create, update, and destroy objects, as well as manage file storage. Using a system of JSON serialization/deserialization, storage is persistent between sessions.

Creation of a command interpreter to manage the hbnb projects

alt text

Description of the project
This is the first step towards building your first full web application: the AirBnB clone. The aim of the project is to deploy a replica of the Airbnb Website using my server. The final version of this project will have:

A command interpreter to manipulate data without a visual interface, like a shell (for development and debugging)
A website (front-end) with static and dynamic functionalities
A comprehensive database to manage the backend functionalities
An API that provides a communication interface between the front and backend of the system.
For this project you will fork this codebase:
update the repository name to AirBnB_clone_v2
update the README.md with your information but don’t delete the initial authors
If you are the owner of this repository, please create a new repository named AirBnB_clone_v2 with the same content of AirBnB_clone
MySQL storage
replace the file storage by a Database storage
map your models to a table in database by using an O.R.M.
alt text

These are the environment variables that need to be declared in order to run any script with the DataBase storage:

- HBNB_ENV: running environment. It can be “dev” or “test” for the moment (“production” soon!)
- HBNB_MYSQL_USER: the username of your MySQL
- HBNB_MYSQL_PWD: the password of your MySQL
- HBNB_MYSQL_HOST: the hostname of your MySQL
- HBNB_MYSQL_DB: the database name of your MySQL
- HBNB_TYPE_STORAGE: the type of storage used. It can be “file” (using ``FileStorage``) or ``db`` (using ``DBStorage``)
Comments for your SQL file:

$ cat my_script.sql
-- first 3 students in the Batch ID=3
-- because Batch 3 is the best!
SELECT id, name FROM students WHERE batch_id = 3 ORDER BY created_at DESC LIMIT 3;
$
Resources
Read or watch:

cmd module
unittest module
args/kwargs
SQLAlchemy tutorial
How To Create a New User and Grant Permissions in MySQL
Python3 and environment variables
SQLAlchemy
MySQL 8.0 SQL Statement Syntax
AirBnB clone - ORM
Repository Contents by Project Task
Tasks	Files	Description
0: Authors/README File	AUTHORS	Project authors
1: Pep8	N/A	All code is pep8 compliant
2: Unit Testing	/tests	All class-defining modules are unittested
3. Make BaseModel	/models/base_model.py	Defines a parent class to be inherited by all model classes
4. Update BaseModel w/ kwargs	/models/base_model.py	Add functionality to recreate an instance of a class from a dictionary representation
5. Create FileStorage class	/models/engine/file_storage.py /models/_ init _.py /models/base_model.py	Defines a class to manage persistent file storage system
6. Console 0.0.1	console.py	Add basic functionality to console program, allowing it to quit, handle empty lines and ^D
7. Console 0.1	console.py	Update the console with methods allowing the user to create, destroy, show, and update stored data
8. Create User class	console.py /models/engine/file_storage.py /models/user.py	Dynamically implements a user class
9. More Classes	/models/user.py /models/place.py /models/city.py /models/amenity.py /models/state.py /models/review.py	Dynamically implements more classes
10. Console 1.0	console.py /models/engine/file_storage.py	Update the console and file storage system to work dynamically with all classes update file storage

General Use
First clone this repository.

Once the repository is cloned locate the "console.py" file and run it as follows:

/AirBnB_clone$ ./console.py
When this command is run the following prompt should appear:
(hbnb)
This prompt designates you are in the "HBnB" console. There are a variety of commands available within the console program.
Commands
* create - Creates an instance based on given class

* destroy - Destroys an object based on class and UUID

* show - Shows an object based on class and UUID

* all - Shows all objects the program has access to, or all objects of a given class

* update - Updates existing attributes an object based on class name and UUID

* quit - Exits the program (EOF will as well)
Alternative Syntax
Users are able to issue a number of console command using an alternative syntax:

Usage: <class_name>.<command>([<id>[name_arg value_arg]|[kwargs]])
Advanced syntax is implemented for the following commands:

* all - Shows all objects the program has access to, or all objects of a given class

* count - Return number of object instances by class

* show - Shows an object based on class and UUID

* destroy - Destroys an object based on class and UUID

* update - Updates existing attributes an object based on class name and UUID

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
Caleb Ini. Duff
Okpara Onyedikachi G


