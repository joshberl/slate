---
title: API Reference

language_tabs:
  - shell
  - ruby

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

<!-- includes:
  - errors
 -->
search: true
---

# Introduction

Welcome to the Reportinc API! You can use our API to access Reportinc API endpoints, which can create, get, and modify events and users.

We have language bindings in Shell and Ruby. You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Events

## Get All Events

Returns all of the events in the database as json

```shell
curl "http://reportinc.herokuapp.com/api/events"
```

> The above command returns JSON structured like this:

```json
{
    "events":[
        {
            "id":114,
            "title":"Russell",
            "description":"",
            "danger":3,
            "prog_level":"Need Assistance",
            "event_date":"2016-05-05",
            "lat":"42.418118",
            "lng":"-71.108858",
            "user_id":1,
            "created_at":"2016-05-05T18:44:56.940Z",
            "avatar_url":null,
            "department":"Events Management"
        },
        {
            "id":113,
            "title":"Russell",
            "description":"",
            "danger":3,
            "prog_level":"Need Assistance",
            "event_date":"2016-05-05",
            "lat":"42.418118",
            "lng":"-71.108858",
            "user_id":1,
            "created_at":"2016-05-05T18:44:56.919Z",
            "avatar_url":null,
            "department":null
        }, 
        ...more_events...
    ]
}
```


### HTTP Request

`GET http://reportinc.herokuapp.com/api/events`

## Get a Specific Event

Returns a specific event, by event ID number as json

```shell
curl "http://reportinc.herokuapp.com/api/events/[ID]"
```
> For example, the command: >
```shell
curl "http://reportinc.herokuapp.com/api/events/1"
``` 
> Would return JSON structured like this:

```json
{
    "event": {
            "id":1,
            "title":"Bon Fire in that there forest",
            "description":"I know that this isn't a forest BUT its dangerous none the less",
            "danger":4,
            "prog_level":"Need Assistance",
            "event_date":"2016-03-02",
            "lat":"51.507351",
            "lng":"-0.127758",
            "user_id":2,
            "created_at":"2016-03-14T17:55:26.494Z",
            "avatar_url":null,
            "department":null
    }
}
```
### HTTP Request

`GET http://reportinc.herokuapp.com/api/events/[ID]`

## Update Event

Updates an existing event given an its ID number, returns the updated JSON of that event

```shell
curl -X PUT -d [key]=[value] "http://reportinc.herokuapp.com/api/events/[ID]"
```

Keys can be: event id, title, description, response time, reports, danger, progress, event date, latitude, longitude, user id

### HTTP Request

`PUT http://reportinc.herokuapp.com/api/events/[ID]`

## Create Event

Creates a new event with the given parameters, returns the JSON of that event

```shell
curl --data "[key1]=[value1]&[key2]=[value2]" "http://reportinc.herokuapp.com/api/events/[ID]"
```

Required fields are: user id, title, event date, latitude, and longitude

### HTTP Request

`POST http://reportinc.herokuapp.com/api/events/`

# Users

## Get User by ID

There is no general GET request for all registered users for privacy reasons. However, you can look up individual users by user ID. This will likely be overhauled once we have implemented more user authentication.

Returns a specific event, by user ID number as json

```shell
curl "http://reportinc.herokuapp.com/api/users/[ID]"
```
> For example, the command: >
```shell
curl "http://reportinc.herokuapp.com/api/users/1"
``` 
> Would return JSON structured like this:

```json
{
    "user": {
        "id":1,
        "first":"Josh",
        "last":"Barl",
        "phone":"5555555555",
        "email":"joshuabarl@tufts.edu",
        "username":"joshbarl",
        "department":"Sustainability",
        "admin":true
    }
}
```

### HTTP Request

`GET http://reportinc.herokuapp.com/api/users/[ID]`

## Update User

Updates an existing user given an their ID number, returns the updated JSON of that user

```shell
curl -X PUT -d [key]=[value] "http://reportinc.herokuapp.com/api/users/[ID]"
```

Keys can be: user id, first name, last name, phone number, email, username, password

### HTTP Request

`PUT http://reportinc.herokuapp.com/api/users/[ID]`

## Create User

Creates a new user with the given parameters, returns the JSON of that user

```shell
curl --data "[key1]=[value1]&[key2]=[value2]" "http://reportinc.herokuapp.com/api/users/[ID]"
```

Required fields are: last name, email, username, and password

### HTTP Request

`POST http://reportinc.herokuapp.com/api/users/`

The same API functions exist for tags, event_tags, event_photos, and sessions