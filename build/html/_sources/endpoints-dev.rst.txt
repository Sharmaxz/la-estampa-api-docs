EndPoints
------------------------

All the endpoints are with pagination in this format:

.. code-block:: bash

    {
        "count": 584,
        "next": "https://la-estampa.herokuapp.com/api/print/?page=4",
        "previous": "https://la-estampa.herokuapp.com/api/print/?page=2",
        "results": [
           …
        ]
    }

The limit per page are 100 elements.

- `More about pagination`_

.. _`More about pagination`: https://www.django-rest-framework.org/api-guide/pagination/


------------------------

Authenticating Requests
-----------------------

You need to authenticate to have permission to access endpoints.


Requesting the bearer token
===========================

.. list-table:: **Attributes**
   :widths: 15 15

   * - client_id
     - client_id

   * - client_secret
     - client_secret

   * - grant_type
     - password

   * - username
     - your email

   * - password
     - your password


.. code-block:: bash

    curl -X POST -d "client_id=<client_id>&client_secret=<client_secret>&grant_type=password&username=<your_username>&password=<your_password>"  https://la-estampa.herokuapp.com/o/token/


**Response

.. code-block:: bash

    {
        "access_token": "<your_access_token>",
        "expires_in": 172800,
        "token_type": "Bearer",
        "scope": "read write",
        "refresh_token": "<your_refresh_token>"
    }

You have access to use the API now.


Refreshing token
================

.. list-table:: **Attributes**
   :widths: 15 15

   * - client_id
     - client_id

   * - client_secret
     - client_secret

   * - grant_type
     - password

   * - refresh_token
     - your refresh token


.. code-block:: bash

    curl -X POST -d "client_id=<client_id>&client_secret=<client_secret>&grant_type=password&refresh_token=<your_refresh_token>"  https://la-estampa.herokuapp.com/o/token/


**Response

.. code-block:: bash

    {
        "access_token": "<your_access_token>",
        "expires_in": 172800,
        "token_type": "Bearer",
        "scope": "read write",
        "refresh_token": "<your_refresh_token>"
    }


------------------------

Briefing
------------------------


.. list-table:: **Attributes**
   :widths: 15 15 15 15
   :header-rows: 1

   * - field
     - type
     - required
     - extension

   * - id
     - integer
     - false
     -

   * - text
     - string
     - true
     -

   * - images
     - file
     - false
     - jpeg, psd

   * - print
     - Print
     - true
     -


GET
===

If you want to get briefing, use:

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/briefing/

**Response:**

.. code-block:: bash

    [
        {
            "id": 1,
            "text": "The best briefing ever"
            "images": []
            "print": 1,
        },
        {
            "id": 2,
            "text": "The second best briefing ever"
            "images": ["briefing/1.jpg", "briefing/2.jpg"]
            "print": 2,

        }
        ...
    ]

But if you prefer to take one briefing. Replace the <id> for the value that you want.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/briefing/<id>/

**Response:**

.. code-block:: bash

        {
            "id": 1,
            "text": "The best briefing ever"
            "images": []
            "print": 1,
        }


POST
====

You need to do post request with the briefing name in the body to create a new.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/briefing/

body:

.. code-block:: bash

    {
        "text": "The best briefing ever"
        "images": []
        "print": 1,
    }


**Response:**

.. code-block:: bash

    {
        "id": 1,
        "text": "The best briefing ever"
        "images": []
        "print": 1,
    }

PUT
===

Choose the briefing that you want to update and replace the <id> to briefing ID and add all the attributes in the body.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/briefing/<id>/

body:

.. code-block:: bash

    {
        "text": "The best briefing ever"
        "images": ["briefing/1.jpg"]
        "print": 1,
    }


**Response:**

.. code-block:: bash

    {
        "id": 1,
        "text": "The best briefing ever"
        "images": ["briefing/1.jpg"]
        "print": 1,
    }

P.S: The response will contains the new values.

PATCH
=====

Choose the briefing that you want to partial update and replace the <id> to briefing ID and add all the attributes in the body.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/briefing/<id>/

body:

.. code-block:: bash

    {
        "print": 2,
    }

**Response:**

.. code-block:: bash

    {
        "id": 1,
        "text": "The best briefing ever"
        "images": ["briefing/1.jpg"]
        "print": 2,
    }

P.S: The response will contains the new values.


------------------------

Category
------------------------

The category is a way to filter and sort the `Tag`_.

.. list-table:: **Attributes**
   :widths: 15 15 15
   :header-rows: 1

   * - field
     - type
     - required

   * - id
     - integer
     - false

   * - name
     - string
     - true

GET
===

If you want to get category, use:

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/category/

**Response:**

.. code-block:: bash

    [
        {
            "id": 1,
            "name": "técnica"
        },
        {
            "id": 2,
            "name": "tema"
        }
        ...
    ]

But if you prefer to take one category. Replace the <id> for the value that you want.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/category/<id>/

**Response:**

.. code-block:: bash

    {
        "id": 1,
        "name": "técnica"
    }


POST
====

You need to do post request with the category name in the body to create a new.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/category/

body:

.. code-block:: bash

    {
        "name" : "cor"
    }


**Response:**

.. code-block:: bash

    {
        "id": 3,
        "name": "cor"
    }

PUT
===

Choose the category that you want to update and replace the <id> to category ID and add all the attributes in the body.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/category/<id>/

body:

.. code-block:: bash

    {
        "name" : "construção"
    }


**Response:**

.. code-block:: bash

    {
        "id": 3,
        "name": "construção"
    }

P.S: The response will contains the new values.

PATCH
=====

Choose the category that you want to partial update and replace the <id> to category ID and add all the attributes in the body.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/category/<id>/

body:

.. code-block:: bash

    {
        "name" : "construção"
    }

**Response:**

.. code-block:: bash

    {
        "id": 1,
        "name": "construção"
    }

P.S: The response will contains the new values.

------------------------

Client
------------------------

The client is a the Print_ owner.

.. list-table:: **Attributes**
   :widths: 15 15 15
   :header-rows: 1

   * - field
     - type
     - required

   * - id
     - integer
     - false

   * - name
     - string
     - true

   * - COD_CLIENTE
     - string
     - false


GET
===

If you want to get client, use:

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/client/

**Response:**

.. code-block:: bash

    [
        {
            "id": 1,
            "name": "Ana",
            "COD_CLIENTE": null
        },
        {
            "id": 2,
            "name": "Carolina",
            "COD_CLIENTE": 12345
        },
        ...
    ]

But if you prefer to take one client. Replace the <id> for the value that you want.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/client/<id>/

**Response:**

.. code-block:: bash

    {
        "id": 1,
        "name": "Ana",
        "COD_CLIENTE": null
    }


POST
====

You need to do post request with the client name in the body to create a new.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/client/

body:

.. code-block:: bash

    {
        "name": "Ana",
        "COD_CLIENTE": null
    }


**Response:**

.. code-block:: bash

    {
        "id": 1,
        "name": "Ana",
        "COD_CLIENTE": null
    }


PUT
===

Choose the client that you want to update and replace the <id> to client ID and add all the attributes in the body.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/client/<id>/

body:

.. code-block:: bash

    {
        "name": "Ana",
        "COD_CLIENTE": 23456
    }


**Response:**

.. code-block:: bash

    {
        "id": 1,
        "name": "Ana",
        "COD_CLIENTE": 23456
    }

P.S: The response will contains the new values.


PATCH
=====

Choose the client that you want to partial update and replace the <id> to client ID and add all the attributes in the body.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/client/<id>/

body:

.. code-block:: bash

    {
        "COD_CLIENTE": 23456
    }

**Response:**

.. code-block:: bash

    {
        "id": 1,
        "name": "Ana",
        "COD_CLIENTE": 23456
    }

P.S: The response will contains the new values.


------------------------

Collection
------------------------

The collection is a `Print`_ group, with the name suggests is a `Print`_ collection.

.. list-table:: **Attributes**
   :widths: 15 15 15
   :header-rows: 1

   * - field
     - type
     - required
     - choices

   * - id
     - integer
     - false
     -

   * - name
     - integer
     - true
     -

   * - date_creation *
     - datetime
     - false
     -

   * - date_update *
     - datetime
     - false
     -

   * - type
     - string
     -
     - COL, ID

   * - briefing
     - string
     - false
     -

   * - ps
     - string
     - false
     -

P.S.: The date_creation and date_update are not required because the value default is the current time.

GET
===

If you want to get collections, use:

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/collection/

**Response:**

.. code-block:: bash

    [
        {
            "id": 1,
            "name": "verão 2019",
            "date_creation": "2018-11-21T12:21:43.862687Z",
            "date_update": "2018-12-20T15:50:25.843449Z",
            "type": 'COL',
            "briefing": "The best briefing ever",
            "ps": ""
        },
        {
            "id": 2,
            "name": "inverno 2019",
            "date_creation": "2018-12-21T12:45:12.232511Z",
            "date_update": "2019-04-01T15:12:53.453569Z",
            "type": 'ID',
            "briefing": "The second best briefing ever",
            "ps": ""
        }
        ...
    ]

And you can order the Collection by **ascending** and **descending** with the query "order".

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/collection/?order=descending

**Response:**

.. code-block:: bash

    [
        {
            "id": 145,
            "name": "verão 2020",
            "date_creation": "2019-12-20T21:35:32.847649Z",
            "date_update": "2019-12-20T20:51:50.843449Z",
            "type": 'COL',
            "briefing": "The one hundred and forty-fifth best briefing ever",
            "ps": ""
        },
        {
            "id": 144,
            "name": "inverno 2020",
            "date_creation": "2019-11-21T19:43:21.862687Z",
            "date_update": null,
            "type": 'COL',
            "briefing": "The hundred and forty-fourth best briefing ever",
            "ps": ""
        }
        ...
    ]



But if you prefer to take one category. Replace the <id> for the value that you want.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/collection/<id>/

**Response:**

.. code-block:: bash

    {
        "id": 1,
        "name": "verão 2019",
        "date_creation": "2018-11-21T12:21:43.862687Z",
        "date_update": "2018-12-20T15:50:25.843449Z",
        "type": 'COL',
        "briefing": "The best briefing ever",
        "ps": ""
    }


POST
====

You need to do post request with the collection attributes in the body to create a new.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/collection/

body:

.. code-block:: bash

    {
        "name": "verão 2019",
        "date_update": "2018-12-20T15:50:25.843449Z",
        "type": 'COL',
        "briefing": "The best briefing ever",
        "ps": ""
    }


**Response:**

.. code-block:: bash

    {
        "id": 1,
        "name": "verão 2019",
        "date_creation": "2018-11-21T12:21:43.862687Z",
        "date_update": "2018-12-20T15:50:25.843449Z",
        "type": 'COL',
        "briefing": "The best briefing ever",
        "ps": ""
    }


PUT
===

Choose the collection that you want to update and replace the <id> to collection ID and add all the attributes in the body.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/collection/<id>/

body:

.. code-block:: bash

    {
        "name": "verão 2020",
        "date_update": "2019-12-20T20:51:50.843449Z",
        "briefing": "Now this the best briefing ever",
        "type": 'COL',
        "ps": ""
    }


**Response:**

.. code-block:: bash

    {
        "id": 145,
        "name": "verão 2020",
        "date_creation": "2019-11-21T19:43:21.862687Z",
        "date_update": "2019-12-20T21:23:12.783479Z",
        "type": 'COL',
        "briefing": "Now this the best briefing ever",
        "ps": ""
    }

P.S: The response will contains the new values.

PATCH
=====

Choose the collection that you want to partial update and replace the <id> to collection ID and add all the attributes in the body.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/collection/<id>/

body:

.. code-block:: bash

    {
        "name" : "outono 2020"
    }

**Response:**

.. code-block:: bash

    {
        "id": 1,
        "name": "outono 2020",
        "date_creation": "2018-11-21T12:21:43.862687Z",
        "date_update": "2019-12-20T21:23:12.783479Z",
        "type": 'COL',
        "briefing": "The best briefing ever",
        "ps": ""
    }

P.S: The response will contains the new values.


------------------------

Feedback
------------------------

The feedback is a print commentary that will have the behavior of a chat on the front end.

.. list-table:: **Attributes**
   :widths: 15 15 15
   :header-rows: 1

   * - field
     - type
     - required

   * - id
     - integer
     - false

   * - print
     - Print
     - true

   * - sender
     - User
     - true

   * - date *
     - datetime
     - false

   * - text
     - string
     - true

   * - data
     - JSONField
     - false

P.S.: The date is not required because the value default is the current time.

GET
===

If you want to get feedback, use:

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/feedback/

**Response:**

.. code-block:: bash

    [
        {
            "id": 1,
            "date": "2019-12-03T14:24:46.605379Z",
            "text": "Could you change the red? Maybe blue.",
            "data": {},
            "print": 1,
            "sender": 1
        },
        {
            "id": 2,
            "date": "2019-12-03T14:30:03.502329Z",
            "text": "Yes, I could, but I wouldn't really want to change to blue, I prefer yellow in this case.",
            "data": {},
            "print": 1,
            "sender": 2
        }
        ...
    ]


And you can order the feedback by **ascending** and **descending** with the query "order".

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/feedback/?order=descending

**Response:**

.. code-block:: bash

    [
        {
            "id": 24,
            "date": "2019-12-03T13:03:30.601202Z",
            "text": "Yes, I knew it. I warned you",
            "data": {},
            "print": 1,
            "sender": 1
        },
        {
            "id": 23,
            "date": "2019-12-03T12:46:24.502605Z",
            "text": "The yellow really was bad.",
            "data": {},
            "print": 1,
            "sender": 2
        }
        ...
    ]


But if you prefer to take one feedback. Replace the <id> for the value that you want.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/feedback/<id>/

**Response:**

.. code-block:: bash

    {
        "id": 1,
        "date": "2019-12-03T14:24:46.605379Z",
        "text": "Could you change the red? Maybe blue.",
        "data": {},
        "print": 1,
        "sender": 1
    }


POST
====

You need to do post request with the feedback attributes in the body to create a new.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/feedback/

body:

.. code-block:: bash

    {
        "text": "Ok, I will change to blue.",
        "data": {},
        "print": 1,
        "sender": 2
    }


**Response:**

.. code-block:: bash

    {
        "id": 25,
        "date": "2019-12-03T13:05:30.601202Z",
        "text": "Ok, I will change to blue.",
        "data": {},
        "print": 1,
        "sender": 2
    }


PUT
===

Choose the feedback that you want to update and replace the <id> to feedback ID and add all the attributes in the body.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/feedback/<id>/

body:

.. code-block:: bash

    {
        "text": "Ok, I will change to blue. I hope this looks cool.",
        "data": {},
        "print": 1,
        "sender": 2
    }


**Response:**

.. code-block:: bash

    {
        "id": 25,
        "date": "2019-12-03T13:05:30.601202Z",
        "text": "Ok, I will change to blue. I hope this looks cool.",
        "data": {},
        "print": 1,
        "sender": 2
    }

P.S: The response will contains the new values.


PATCH
=====

Choose the feedback that you want to partial update and replace the <id> to feedback ID and add all the attributes in the body.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/feedback/<id>/

body:

.. code-block:: bash

    {
        "text": "Ok, I will change to blue. I hope this looks cool.",
    }

**Response:**

.. code-block:: bash

    {
        "id": 25,
        "date": "2019-12-03T13:05:30.601202Z",
        "text": "Ok, I will change to blue. I hope this looks cool.",
        "data": {},
        "print": 1,
        "sender": 2
    }

P.S: The response will contains the new values.


------------------------

Notification
------------------------


.. list-table:: **Attributes**
   :widths: 15 15 15
   :header-rows: 1

   * - field
     - type
     - required

   * - id
     - integer
     - false

   * - sender
     - User
     - true

   * - receiver
     - User
     - true

   * - date *
     - datetime
     - false

   * - viewed
     - boolean
     - false

   * - message
     - string
     - true

P.S.: The date is not required because the value default is the current time.


GET
===

If you want to get notification, use:

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/notification/

**Response:**

.. code-block:: bash

    [
        {
            "id": 1,
            "date": "2020-01-28T16:18:26.186210Z",
            "viewed": false,
            "message": "Hi",
            "sender": 1,
            "receiver": 7
        },
        {
            "id": 2,
            "date": "2020-01-28T16:19:53.153214Z",
            "viewed": false,
            "message": "Hello",
            "sender": 7,
            "receiver": 1
        },
        ...
    ]


.. code-block:: bash

    https://la-estampa.herokuapp.com/api/notification/<id>/

**Response:**

.. code-block:: bash

    {
        "id": 1,
        "date": "2020-01-28T16:18:26.186210Z",
        "viewed": false,
        "message": "Hi",
        "sender": 1,
        "receiver": 7
    }


POST
====

You need to do post request with the notification attributes in the body to create a new.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/notification/

body:

.. code-block:: bash

    {
        "viewed": false,
        "message": "Hi",
        "sender": 1,
        "receiver": 7
    }


**Response:**

.. code-block:: bash

    {
        "id": 1,
        "date": "2020-01-28T16:18:26.186210Z",
        "viewed": false,
        "message": "Hi",
        "sender": 1,
        "receiver": 7
    }


PUT
===

Choose the notification that you want to update and replace the <id> to notification ID and add all the attributes in the body.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/notification/<id>/

body:

.. code-block:: bash

    {
        "viewed": true,
        "message": "Hello",
        "sender": 1,
        "receiver": 7
    }

**Response:**

.. code-block:: bash

    {
        "id": 1,
        "date": "2020-01-28T16:18:26.186210Z",
        "viewed": true,
        "message": "Hello",
        "sender": 1,
        "receiver": 7
    }

P.S: The response will contains the new values.


PATCH
=====

Choose the notification that you want to partial update and replace the <id> to notification ID and add all the attributes in the body.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/notification/<id>/

body:

.. code-block:: bash

    {
        "message": "Hello",
    }

**Response:**

.. code-block:: bash

    {
        "id": 1,
        "date": "2020-01-28T16:18:26.186210Z",
        "viewed": true,
        "message": "Hello",
        "sender": 1,
        "receiver": 7
    }

P.S: The response will contains the new values.


------------------------

Print
------------------------

The print is the main model. It have `home`_ endpoint that is your light version.

.. list-table:: **Attributes**
   :widths: 15 15 15 15 15
   :header-rows: 1

   * - field
     - type
     - required
     - extension
     - choices

   * - id
     - integer
     - false
     -
     -

   * - owner
     - Client
     - false
     -
     -

   * - designer
     - User
     - false
     -
     -

   * - coordinator
     - User
     - false
     -
     -

   * - collection
     - Collection
     - false
     -
     -

   * - code
     - string
     - false
     -
     -

   * - status
     - string
     - false
     -
     - APP, REV, DEN, SKE

   * - type
     - string
     - false
     -
     - DIG, CYL, BOTH

   * - exclusivity
     - string
     - false
     -
     - INT, NAT, REG, VIN

   * - exclusivity_int
     - string
     - false
     -
     - Acronym of all countries in the world

   * - exclusivity_reg
     - string
     - false
     -
     - Acronym of all brazil states

   * - exclusivity_other
     - string
     - false
     -
     -

   * - expire
     - boolean
     - false
     -
     -


   * - date_creation *
     - datetime
     - true
     -
     -

   * - date_update *
     - datetime
     - false
     -
     -

   * - date_approved
     - datetime
     - false
     -
     -

   * - date_expiration
     - datetime
     - false
     -
     -

   * - origin
     - Print
     - false
     -
     -

   * - is_origin
     - boolean
     - false
     -
     -

   * - is_twin
     - boolean
     - false
     -
     -

   * - dpi
     - float
     - false
     -
     -

   * - image
     - file
     - false
     - jpeg
     -

   * - psd_original
     - file
     - false
     - psd
     -

   * - psd_final
     - file
     - false
     - psd
     -

   * - psd_flirted
     - file
     - false
     - psd
     -

   * - rapport
     - string
     - false
     -
     -

   * - rapport_direction
     - boolean
     - false
     -
     -

P.S.: The date_request and date_update are not required because the value default is the current time.

GET
===

If you want to get print, use:

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/print/

**Response:**

.. code-block:: bash

    [
        {
            "id": 1,
            "tagprint_set": [
                {
                    "tag": {
                        "id": 1,
                        "name": "aquarela",
                        "category": 1
                    }
                }
            ],
            "briefing_set": [],
            "code": "L12345",
            "status": "APP",
            "type": null,
            "exclusivity": "REG",
            "exclusivity_int": [],
            "exclusivity_reg": [
                "SP"
            ],
            "exclusivity_other": null,
            "expire": true,
            "date_creation": "2019-10-01T00:00:00Z",
            "date_update": "2019-10-01T00:00:00Z",
            "date_approved": "2019-11-19T00:00:00Z",
            "date_expiration": null,
            "is_origin": true,
            "is_twin": false,
            "dpi": null,
            "image": "print/small/L12345.jpg"
            "psd_original": "print/psd/original/L12345.psd",
            "psd_final": null,
            "psd_flirted": null,
            "rapport": "",
            "rapport_direction": false,
            "owner": null,
            "designer": 7,
            "coordinator": 6,
            "collection": null,
            "origin": null
        },
        {
            "id": 2,
            "tagprint_set": [
                {
                    "tag": {
                        "id": 27,
                        "name": "Figurativo",
                        "category": 3
                    }
                }
            ],
            "briefing_set": [],
            "code": "L12346",
            "status": "APP",
            "type": null,
            "exclusivity": "INT",
            "exclusivity_int": [],
            "exclusivity_reg": [],
            "exclusivity_other": null,
            "expire": false,
            "date_creation": "2019-10-01T00:00:00Z",
            "date_update": "2019-10-01T00:00:00Z",
            "date_approved": "2019-10-01T00:00:00Z",
            "date_expiration": null,
            "is_origin": true,
            "is_twin": false,
            "dpi": null,
            "image": null,
            "psd_original": null,
            "psd_final": null,
            "psd_flirted": null,
            "rapport": "",
            "rapport_direction": false,
            "owner": null,
            "designer": 7,
            "coordinator": 7,
            "collection": null,
            "origin": null
        },
        ...
    ]

But if you prefer to take one reserve. Replace the <id> for the value that you want.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/print/<id>/

**Response:**

.. code-block:: bash

    {
        "id": 1,
        "tagprint_set": [
            {
                "tag": {
                    "id": 1,
                    "name": "aquarela",
                    "category": 1
                }
            }
        ],
        "briefing_set": [],
        "code": "L12345",
        "status": "APP",
        "type": null,
        "exclusivity": "REG",
        "exclusivity_int": [],
        "exclusivity_reg": [
            "SP"
        ],
        "exclusivity_other": null,
        "expire": false,
        "date_creation": "2019-10-01T00:00:00Z",
        "date_update": "2019-10-01T00:00:00Z",
        "date_approved": "2019-11-19T00:00:00Z",
        "date_expiration": null,
        "is_origin": true,
        "is_twin": false,
        "dpi": null,
        "image": "print/small/L12345.jpg"
        "psd_original": "print/psd/original/L12345.psd",
        "psd_final": null,
        "psd_flirted": null,
        "rapport": "",
        "rapport_direction": false,
        "owner": null,
        "designer": 7,
        "coordinator": 6,
        "collection": null,
        "origin": null
    }


POST
====

You need to do post request with the print attributes in the body to create a new.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/print/

body:

.. code-block:: bash

     {
        "tagprint_set": [
            {
                "tag": {
                    "id": 1,
                    "name": "aquarela",
                    "category": 1
                }
            }
        ],
        "briefing_set": [],
        "code": "L12345",
        "status": "APP",
        "type": null,
        "exclusivity": "REG",
        "exclusivity_int": [],
        "exclusivity_reg": [
            "SP"
        ],
        "exclusivity_other": null,
        "expire": false,
        "date_creation": "2019-10-01T00:00:00Z",
        "date_update": "2019-10-01T00:00:00Z",
        "date_approved": "2019-11-19T00:00:00Z",
        "date_expiration": null,
        "is_origin": true,
        "is_twin": false,
        "dpi": null,
        "image": "print/small/L12345.jpg"
        "psd_original": "print/psd/original/L12345.psd",
        "psd_final": null,
        "psd_flirted": null,
        "rapport": "",
        "rapport_direction": false,
        "owner": null,
        "designer": 7,
        "coordinator": 6,
        "collection": null,
        "origin": null
     },


**Response:**

.. code-block:: bash

    {
        "id": 1,
        "tagprint_set": [
            {
                "tag": {
                    "id": 1,
                    "name": "aquarela",
                    "category": 1
                }
            }
        ],
        "briefing_set": [],
        "code": "L12345",
        "status": "APP",
        "type": null,
        "exclusivity": "REG",
        "exclusivity_int": [],
        "exclusivity_reg": [
            "SP"
        ],
        "exclusivity_other": null,
        "expire": false,
        "date_creation": "2019-10-01T00:00:00Z",
        "date_update": "2019-10-01T00:00:00Z",
        "date_approved": "2019-11-19T00:00:00Z",
        "date_expiration": null,
        "is_origin": true,
        "is_twin": false,
        "dpi": null,
        "image": "print/small/L12345.jpg"
        "psd_original": "print/psd/original/L12345.psd",
        "psd_final": null,
        "psd_flirted": null,
        "rapport": "",
        "rapport_direction": false,
        "owner": null,
        "designer": 7,
        "coordinator": 6,
        "collection": null,
        "origin": null
     },


PUT
===

Choose the print that you want to update and replace the <id> to tag ID and add all the attributes in the body.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/print/<id>/

body:

.. code-block:: bash

    {
        "tagprint_set": [
            {
                "tag": {
                    "id": 1,
                    "name": "aquarela",
                    "category": 1
                }
            }
        ],
        "briefing_set": [
            {
                "id": 1,
                "text": "the best briefing ever",
                "images": "briefing/1.jpg",
                "print": 1
            }
        ],
               "code": "L12345",
        "status": "APP",
        "type": null,
        "exclusivity": "REG",
        "exclusivity_int": [],
        "exclusivity_reg": [
            "SP"
        ],
        "exclusivity_other": null,
        "expire": false,
        "date_creation": "2019-10-01T00:00:00Z",
        "date_update": "2019-10-01T00:00:00Z",
        "date_approved": "2019-11-19T00:00:00Z",
        "date_expiration": null,
        "is_origin": true,
        "is_twin": false,
        "dpi": null,
        "image": "print/small/L12345.jpg"
        "psd_original": "print/psd/original/L12345.psd",
        "psd_final": null,
        "psd_flirted": null,
        "rapport": "",
        "rapport_direction": false,
        "owner": null,
        "designer": 7,
        "coordinator": 6,
        "collection": null,
        "origin": null
     },




**Response:**

.. code-block:: bash

    {
        "id": 1
        "tagprint_set": [
            {
                "tag": {
                    "id": 1,
                    "name": "aquarela",
                    "category": 1
                }
            }
        ],
        "briefing_set": [
            {
                "id": 1,
                "text": "the best briefing ever",
                "images": "briefing/1.jpg",
                "print": 1
            }
        ],
               "code": "L12345",
        "status": "APP",
        "type": null,
        "exclusivity": "REG",
        "exclusivity_int": [],
        "exclusivity_reg": [
            "SP"
        ],
        "exclusivity_other": null,
        "expire": false,
        "date_creation": "2019-10-01T00:00:00Z",
        "date_update": "2019-10-01T00:00:00Z",
        "date_approved": "2019-11-19T00:00:00Z",
        "date_expiration": null,
        "is_origin": true,
        "is_twin": false,
        "dpi": null,
        "image": "print/small/L12345.jpg"
        "psd_original": "print/psd/original/L12345.psd",
        "psd_final": null,
        "psd_flirted": null,
        "rapport": "",
        "rapport_direction": false,
        "owner": null,
        "designer": 7,
        "coordinator": 6,
        "collection": null,
        "origin": null
     },

P.S: The response will contains the new values.


PATCH
=====

Choose the print that you want to partial update and replace the <id> to reserve ID and add all the attributes in the body.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/print/<id>/

body:

.. code-block:: bash

    {
        "status": "REV",
        "psd_final": "print/psd/final/L12345.psd",
    }

**Response:**

.. code-block:: bash

    {
        "id": 1
        "tagprint_set": [
            {
                "tag": {
                    "id": 1,
                    "name": "aquarela",
                    "category": 1
                }
            }
        ],
        "briefing_set": [
            {
                "id": 1,
                "text": "the best briefing ever",
                "images": "briefing/1.jpg",
                "print": 1
            }
        ],
               "code": "L12345",
        "status": "REV",
        "exclusivity_other": null,
        "expire": false,
        "date_creation": "2019-10-01T00:00:00Z",
        "date_update": "2019-10-01T00:00:00Z",
        "date_approved": "2019-11-19T00:00:00Z",
        "date_expiration": null,
        "is_origin": true,
        "is_twin": false,
        "dpi": null,
        "image": "print/small/L12345.jpg"
        "psd_original": "print/psd/original/L12345.psd",
        "psd_final": null,
        "psd_flirted": null,
        "rapport": "",
        "rapport_direction": false,
        "owner": null,
        "designer": 7,
        "coordinator": 6,
        "collection": null,
        "origin": null
     },

P.S: The response will contains the new values.

HOME
====

The home endpoint is a light version of the print GET method and don't accepted another method type.

GET
...
.. code-block:: bash

    https://la-estampa.herokuapp.com/api/home/

**Response:**

.. code-block:: bash

    [
        {
            "image": "/print/small/L231323.jpg"
            "code": "L231323",
            "status": "REV",
            "exclusivity": "none",
            "collection": null,
            "type": "DIG"
        },
        {
            "image": "/print/small/L12345.jpg"
            "code": "L12345",
            "status": "APP",
            "exclusivity": "NAT",
            "collection": 2,
            "type": "DIG"
        }
        ...
    ]

------------------------

Reserve
------------------------

The print reserve.

.. list-table:: **Attributes**
   :widths: 15 15 15
   :header-rows: 1

   * - field
     - type
     - required

   * - id
     - integer
     - false

   * - seller
     - User
     - false


   * - client
     - Client
     - false

   * - print
     - Print
     - false

   * - date_request *
     - datetime
     - false

   * - date_end
     - datetime
     - true

P.S.: The date_request is not required because the value default is the current time.


GET
===

If you want to get reserve, use:

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/reserve/

**Response:**

.. code-block:: bash

    [
        {
            "id": 1,
            "clerk": 1,
            "print": 1,
            "date_request": "2019-12-03T13:45:31.601412Z",
            "date_end": "2020-01-15T23:59:59.699999Z",
        },
        {
            "id": 2,
            "clerk": 1,
            "print": 2,
            "date_request": "2019-12-06T11:53:35.615421Z",
            "date_end": "2019-12-20T23:59:59.699999Z",
        }
        ...
    ]

But if you prefer to take one reserve. Replace the <id> for the value that you want.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/reserve/<id>/

**Response:**

.. code-block:: bash

    {
        "id": 1,
        "clerk": 1,
        "print": 1,
        "date_request": "2019-12-03T13:45:31.601412Z",
        "date_end": "2020-01-15T23:59:59.699999Z",
    }

POST
====

You need to do post request with the reserve attributes in the body to create a new.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/reserve/

body:

.. code-block:: bash

    {
        "clerk": 1,
        "print": 1,
        "date_end": "2020-01-15T23:59:59.699999Z",
    }


**Response:**

.. code-block:: bash

    {
        "id": 1,
        "clerk": 1,
        "print": 1,
        "date_request": "2019-12-03T13:45:31.601412Z",
        "date_end": "2020-01-15T23:59:59.699999Z",
    }

PUT
===

Choose the reserve that you want to update and replace the <id> to tag ID and add all the attributes in the body.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/reserve/<id>/

body:

.. code-block:: bash

    {
        "clerk": 2,
        "print": 1,
        "date_end": "2020-01-20T23:59:59.699999Z",
    }


**Response:**

.. code-block:: bash

    {
        "id": 1,
        "clerk": 2,
        "print": 1,
        "date_request": "2019-12-03T13:45:31.601412Z",
        "date_end": "2020-01-20T23:59:59.699999Z",
    }

P.S: The response will contains the new values.

PATCH
=====

Choose the reserve that you want to partial update and replace the <id> to reserve ID and add all the attributes in the body.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/reserve/<id>/

body:

.. code-block:: bash

    {
        "clerk": 2,
        "print": 1,
        "date_end": "2020-01-20T23:59:59.699999Z",
    }

**Response:**

.. code-block:: bash

    {
        "id": 1,
        "clerk": 2,
        "print": 1,
        "date_request": "2019-12-03T13:45:31.601412Z",
        "date_end": "2020-01-20T23:59:59.699999Z",
    }

P.S: The response will contains the new values.


------------------------

Tag
------------------------

The tag is a representation of contents inside of a print.

.. list-table:: **Attributes**
   :widths: 15 15 15
   :header-rows: 1

   * - field
     - type
     - required

   * - id
     - integer
     - false

   * - name
     - string
     - true

   * - category
     - Category
     - true


GET
===

If you want to get tags, use:

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/tag/

**Response:**

.. code-block:: bash

    [
        {
            "id": 1,
            "name": "floral",
            "category": 1,
        },
        {
            "id": 2,
            "name": "listras",
            "category": 1,
        }
        ...
    ]


And you can order the tag by **ascending** and **descending** alphabetical order with the query "order" or use the query "category" to filter by category.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/tag/?order=descending

**Response:**

.. code-block:: bash

    [
        {
            "id": 12,
            "name": "aquarela",
            "category": 3,

        },
        {
            "id": 20,
            "name": "azulejos",
            "category": 5,
        }
        ...
    ]


But if you prefer to take one feedback. Replace the <id> for the value that you want.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/tag/<id>/

**Response:**

.. code-block:: bash

    {
        "id": 1,
        "name": "floral",
        "category": 1,
    }

POST
====

You need to do post request with the tag attributes in the body to create a new.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/tag/

body:

.. code-block:: bash

    {
        "name": "floral",
        "category": 1,
    }


**Response:**

.. code-block:: bash


    {
        "id": 1,
        "name": "floral",
        "category": 1,
    }


PUT
===

Choose the tag that you want to update and replace the <id> to tag ID and add all the attributes in the body.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/tag/<id>/

body:

.. code-block:: bash

    {
        "name": "floral",
        "category": 2,
    }


**Response:**

.. code-block:: bash

    {
        "id": 1,
        "name": "floral",
        "category": 2,
    }

P.S: The response will contains the new values.


PATCH
=====

Choose the tag that you want to partial update and replace the <id> to tag ID and add all the attributes in the body.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/tag/<id>/

body:

.. code-block:: bash

    {
        "name": "abstrato",
    }

**Response:**

.. code-block:: bash

    {
        "id": 1,
        "name": "abstrato",
        "category": 1,
    }

P.S: The response will contains the new values.

------------------------

User
------------------------

The User is who have permission to see the content of La Estampa.

.. list-table:: **Attributes**
   :widths: 15 15 15
   :header-rows: 1

   * - field
     - type
     - required

   * - id
     - integer
     - false

   * - name
     - string
     - true

   * - email
     - string
     - true

   * - role
     - ArrayField of string
     - false

   * - password *
     - string
     - true

P.S.: The password is only writeable


GET
===

If you want to get user, use:

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/user/

**Response:**

.. code-block:: bash

    [
        {
            "id": 1,
            "name": "Fernando",
            "email": "fernando@laestampa.com.br",
            "role": [
                "designer",
                "coordinator"
            ]
        },
        {
            "id": 2,
            "name": "Jessica",
            "email": "jessica@laestampa.com.br",
            "role": [
                "designer"
            ]
        }
        ...
    ]


But if you prefer to take one user. Replace the <id> for the value that you want.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/user/<id>/

**Response:**

.. code-block:: bash

    {
        "id": 1,
        "name": "Fernando",
        "email": "fernando@laestampa.com.br",
        "role": [
            "designer",
            "coordinator"
        ]
    }


POST
====

You need to do post request with the user attributes in the body to create a new.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/user/

body:

.. code-block:: bash

    {
        "name": "Fernando",
        "email": "fernando@laestampa.com.br",
        "role": [
            "designer",
            "coordinator"
        ]
    }


**Response:**

.. code-block:: bash


    {
        "id": 1,
        "name": "Fernando",
        "email": "fernando@laestampa.com.br",
        "role": [
            "designer",
            "coordinator"
        ]
    }


PUT
===

Choose the user that you want to update and replace the <id> to user ID and add all the attributes in the body.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/user/<id>/

body:

.. code-block:: bash


    {
        "name": "Fernando",
        "email": "fernando@laestampa.com.br",
        "role": [
            "designer"
        ]
    }


**Response:**

.. code-block:: bash

    {
        "id": 1,
        "name": "Fernando",
        "email": "fernando@laestampa.com.br",
        "role": [
            "designer"
        ]
    }

P.S: The response will contains the new values.


PATCH
=====

Choose the user that you want to partial update and replace the <id> to user ID and add all the attributes in the body.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/user/<id>/

body:

.. code-block:: bash

    {
        "role": [
            "coordinator"
        ]
    }

**Response:**

.. code-block:: bash

    {
        "id": 1,
        "name": "Fernando",
        "email": "fernando@laestampa.com.br",
        "role": [
            "coordinator"
        ]
    }

P.S: The response will contains the new values.

------------------------



