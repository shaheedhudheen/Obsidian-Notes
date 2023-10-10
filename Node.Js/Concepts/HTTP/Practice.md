
we are building a photo-collection site.

We want to make an API to keep track of users, venues, and photos of those venues.

This site has an `index.html` and a `style.css`.

Each user has a username and a password. 

Each photo has a venue and an owner (i.e. the user who took the picture).

Each venue has a name and street address.

Can you design a REST system that would accommodate:

- storing users, photos, and venues
- accessing venues and accessing certain photos of a certain venue

Start by writing out:

- what kinds of requests we would want to make
- what responses the server should return
- what the `content-type` of each response should be


## Models

**User** - username and password

```
{  
  “user”: {  
    "id": <Integer>,  
    “username”: <String>,  
    “password”:  <String>  
  }  
}
```

**Photos** -  Venue and Author

```
{  
  “photo”: {  
    "id": <Integer>,  
    “venue_id”: <Integer>,  
    “author_id”: <Integer>  
  }  
}
```


**Venue** -  name and street address

```
{  
  “venue”: {  
    "id": <Integer>,  
    “name”: <String>,  
    “address”: <String>  
  }  
}
```


## Requests/Responses

#### GET Requests

*get html*
Request- `GET /index.html` Accept: `text/html` 
Response- 200 (OK) Content-type: `text/html`

*get css*
Request- `GET /style.css` Accept: `text/css` 
Response- 200 (OK) Content-type: `text/css`

*get Venue List*
Request- `GET /venues` Accept:`application/json` 
Response- 200 (OK) Content-type: `application/json`

*get venue*
Request- `GET /venues/:id` Accept: `application/json` 
Response- 200 (OK) Content-type: `application/json`

*get photo of specific venue*
Request- `GET /venues/:id/photos/:id` Accept: `application/json` 
Response- 200 (OK) Content-type: `image/png`

#### POST Requests

Request- `POST /users` 
Response- 201 (CREATED) Content-type: `application/json`

Request- `POST /venues` 
Response- 201 (CREATED) Content-type: `application/json`

Request- `POST /venues/:id/photos` 
Response- 201 (CREATED) Content-type: `application/json`

#### PUT Requests

Request- `PUT /users/:id` 
Response- 200 (OK)

Request- `PUT /venues/:id` 
Response- 200 (OK)

Request- `PUT /venues/:id/photos/:id` 
Response- 200 (OK)

#### DELETE Requests

Request- `DELETE /venues/:id` 
Response- 204 (NO CONTENT)

Request- `DELETE /venues/:id/photos/:id` 
Response- 204 (NO CONTENT)

