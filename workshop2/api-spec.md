## Shelter API Description

This document describes the service endpoints that you will develop during this workshop.

### Common REST pattern

The api follows a rest pattern common to many services. There are two aspects
to this pattern:
1. The url structure
2. The HTTP actions available for each url.

Let's first investigate the url structure.

    api/v{apiVersion}/{itemsName}
    api/v{apiVersion}/{itemsName}/{id}

* `apiVersion` refers to the version of the data structure that any data supplied to or returned by the api should take.
* `itemsName` describes the type of data items (the plural form of the word is usually used) that this api
returns.
* `id` is the identifier of a specific data item.

The common rest pattern usually supports the following HTTP action types for each of those urls.

* `api/v{x}/{itemsName}`
  * `GET` - Gets a list of data items.
  * `POST` - Creates a new data item.
* `api/v{x}/{itemsName}/{id}`
  * `GET` - Get the item with the given id.
  * `PUT` - Update the item with the given id.
  * `DELETE` - Delete the item with the given id.

### Our implementation

For the Shelter API, two implementations of the abovementioned common REST pattern is needed. One related to pets and another related to inquiries. Since this is the first version of the API the version value should be 1. That means we end up with url structures like this:

    api/v1/pets
    api/v1/pets/{id}
    api/v1/inquiries
    api/v1/inquiries/{id}

### Sample Requests/Responses

TODO: Add more examples.

#### Sample HTTP request and response for getting a list of pets

```HTTP
GET /api/v1/pets HTTP/1.1
```

```HTTP
HTTP/1.1 200 OK
Date: Tue, 25 Feb 2020 17:00:48 GMT
Content-Type: application/json; charset=utf-8
Server: Kestrel
Content-Length: 1542

[{"id":"48dec6816c0b467e9c3a4338018a3e78","name":"Pepper","status":"available","kind":"cat","breed":"Burmese","description":"Pepper is a shy but loving boy who would do best in a quiet family home without other animals or young children.","birthday":"2018-12-07T00:00:00","photos":["https://upload.wikimedia.org/wikipedia/commons/5/5c/British_burmese_-_Andel_Alois_at_Cat_show.JPG"]},{"id":"ae3a25c306bc415eb7d956ae8df5edc1","name":"Fido","status":"available","kind":"dog","breed":"Labrador","description":"Fido is a good boy who loves long walks in the park, playing with his ball and licking faces. He's great with children and an absolute sweetheart.","birthday":"2016-04-15T00:00:00","photos":["https://upload.wikimedia.org/wikipedia/commons/b/b3/Labrador_on_Quantock_%282307909488%29.jpg"]},{"id":"11d6cdeb0bdb4da29d0f7bb688bfaebb","name":"Sasha","status":"unavailable","kind":"cat","breed":"Russian Blue","description":"Sasha was recently rescued by the shelter, and will need some weeks before she's ready to move into her forever home.","birthday":"2016-08-27T00:00:00","photos":["https://upload.wikimedia.org/wikipedia/commons/7/7b/Cat_Janna.jpg"]},{"id":"ce0659f309994feea1df17991594df03","name":"Mika","status":"available","kind":"dog","breed":"German Shepherd","description":"Mika is exactly the kind of dog you want to have in your life: loyal, friendly, playful and gentle around kids and old people.","birthday":"2015-06-10T00:00:00","photos":["https://upload.wikimedia.org/wikipedia/commons/a/a9/Female_German_Shepherd.jpg"]}]```
```
