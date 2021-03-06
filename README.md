[![Codacy Badge](https://api.codacy.com/project/badge/Grade/3d11e47a4cba4e2681327ad8de1bc8b7)](https://www.codacy.com/app/ProberI/CP-2-Bucketlist-Application?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=ProberI/CP-2-Bucketlist-Application&amp;utm_campaign=Badge_Grade)
[![CircleCI](https://circleci.com/gh/paulupendo/CP-2-Bucketlist-Application.svg?style=svg)](https://circleci.com/gh/paulupendo/CP-2-Bucketlist-Application)
[![PEP8](https://img.shields.io/badge/code%20style-pep8-orange.svg)](https://www.python.org/dev/peps/pep-0008/)
[![Codacy Badge](https://api.codacy.com/project/badge/Coverage/3d11e47a4cba4e2681327ad8de1bc8b7)](https://www.codacy.com/app/ProberI/CP-2-Bucketlist-Application?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=ProberI/CP-2-Bucketlist-Application&amp;utm_campaign=Badge_Coverage)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
# Bonne Vie : A Bucketlist API
 
## Introduction
A Bucket List is a list of things that one has not done before but wants to do before dying. Bonne Vie is an api for online bucket list service using Flask. Bonne vie allows you to interact with the api and perform CRUD (Create, Read, Update, Delete) operations on the bucket list.
 
## Installation
 
Clone the Bonne Vie’s GitHub repo:
 
http:
>`$ git clone https://github.com/ProberI/CP-2-Bucketlist-Application.git`

cd into the created folder and install a [virtual environment](https://virtualenv.pypa.io/en/stable/)

`$ virtualenv venv`

Activate the virtual environment

`$ venv/bin/activate`

Install all app requirements

`$ pip install -r requirements.txt`
Create the database and run migrations

`$ createdb bucketlist_db`

> If testing do : 
`$ createdb test_db`

`$ python manage.py db init`

`$ python manage.py db migrate`

`$ python manage.py db upgrade`

All done! Now, start your server by running `python manage.py runserver`. For best experience, use a GUI platform like [postman](https://www.getpostman.com/) to make requests to the api.

### Endpoints

Here is a list of all the endpoints in bucketlist app.

Endpoint | Functionality| Access
------------ | ------------- | ------------- 
POST bucketlist/app/v1/auth/login |Logs a user in | PUBLIC
POST bucketlist/app/v1/auth/register | Registers a user | PUBLIC
POST bucketlist/app/v1/bucketlists/ | Creates a new bucket list | PRIVATE
GET bucketlist/app/v1/bucketlists/ | Lists all created bucket lists | PRIVATE
GET bucketlist/app/v1/bucketlists/id | Gets a single bucket list with the suppled id | PRIVATE
PUT bucketlist/app/v1/bucketlists/id | Updates bucket list with the suppled id | PRIVATE
DELETE bucketlist/app/v1/bucketlists/id | Deletes bucket list with the suppled id | PRIVATE
POST bucketlist/app/v1/bucketlists/id/items/ | Creates a new item in bucket list | PRIVATE
PUT bucketlist/app/v1/bucketlists/id/items/item_id | Updates a bucket list item | PRIVATE
DELETE bucketlist/app/v1/bucketlists/id/items/item_id | Deletes an item in a bucket list | PRIVATE
### Features:
* Search by name
* Pagination
* Token based authentication
### Searching

It is possible to search bucketlists using the parameter `q` in the GET request. 
Example:

`GET http://localhost:/bucketlists?q=Before I get to 30`

This request will return all bucketlists with `Before I get to 30` in their name.

### Pagination

It is possible to limit the count of bucketlist data displayed using the parameter `limit` in the GET request. 
Example:

`GET http://localhost:/bucketlists?limit=5`

### Sample GET response
After a successful resgistration and login, you will receive an athentication token. Pass this token in your request header.
Below is a sample of a GET request for bucketlist

```
{
	id: 1,
	name: “BucketList1”,
	items: [
		{
id: 1,
name: “I need to do X”,
date_created: “2015-08-12 11:57:23”,
date_modified: “2015-08-12 11:57:23”,
done: False
}
]
	date_created: “2015-08-12 11:57:23”,
	date_modified: “2015-08-12 11:57:23”
	created_by: “1113456”
}

```

### Testing
The application tests are based on python’s unit testing framework unittest.
To run tests with nose, run `nosetests`

### License
The API uses an MIT license
