## Event-API

([DEMO](https://youtu.be/VgdJlVD5zXc))


Used:  Laravel Sanctum for API authentication 

db name: event-api
username: root
password: root



Steps to run for checking code functionality:
	
     -> npm install
	
     -> composer install

	-> In the terminal root folder run:
		-> docker compose up

	-> php artisan migrate

	-> php artisan migrate:fresh --seed

	-> php artisan serve



In POSTMAN:

	{{BASE_URL}}  = http://127.0.0.1:8000/api/


	Headers need to be set to    key = Accept        value = application/json

	JSON body:  name, description, start_time, end_time 

	For includes $relations:  Params need to be set to key = include    value = user,attendees,attendees.user    



	endpoints:

	-> {{BASE_URL}}login     POST  logs in with authentication  (need raw JSON login details, eg. email, password)   -> returns the token


	-> {{BASE_URL}}user	  GET the info of the current logged in user  (needs Authorization to be set to "Bearer Token", and the user token from above)


	-> {{BASE_URL}}logout      POST   to log out the currently logged in user   (requires token) 


	-> {{BASE_URL}}events        GET all events   (does not require Auth token !!)


	-> {{BASE_URL}}events/"any_event_number"       GET  to get any event   (requires token) 


	-> {{BASE_URL}}events/        POST to add an event      (name, start_time, end_time)   (requires token) 


	-> {{BASE_URL}}events/"any_event_number"        PUT to an event    (needs JSON raw data, eg. name)


	-> {{BASE_URL}}events/  	DELETE an event


	-> {{BASE_URL}}events?include=user        POST    (traits)  -> posts while including the user information


	-> {{BASE_URL}}events/200/attendees      GET the attendees for the event_id 200


	-> {{BASE_URL}}events?include=user,attendees,attendees.user    GET attendees, include the user info, attendees for that event, and attendees user info
