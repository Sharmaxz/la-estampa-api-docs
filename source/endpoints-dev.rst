Authenticating Requests
-----------------------

You need to authenticate to have permission to access endpoints.


Requesting the bearer token
===========================

.. list-table:: **Attributes**
   :widths: 15 15

   * - client_id
     -

   * - client_secret
     -

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
        "access_token": "AvjYU4gkGAHPfkod66XnKNyxGNvmE0",
        "expires_in": 172800,
        "token_type": "Bearer",
        "scope": "read write",
        "refresh_token": "1qGSwwkU2TggY7LAQL6jIMcyTBcYGf"
    }

You have access to use the API now.



Refreshing token
================

.. list-table:: **Attributes**
   :widths: 15 15
   :header-rows: 1

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

If you want to get all briefing, use:

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

You need to do post request with the briefing name in the body to create a new briefing.

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

If you want to get all categories, use:

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

You need to do post request with the category name in the body to create a new category.

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

Collection
------------------------

The collection is a `Print`_ group, with the name suggests is a `Print`_ collection.

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
     - integer
     - true

   * - date_creation *
     - datetime
     - false

   * - date_update *
     - datetime
     - false

   * - briefing
     - string
     - false

   * - ps
     - string
     - false

P.S.: The date_creation and date_update are not required because the value default is the current time.

GET
===

If you want to get all collections, use:

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
            "briefing": "The best briefing ever",
            "ps": ""
        },
        {
            "id": 2,
            "name": "inverno 2019",
            "date_creation": "2018-12-21T12:45:12.232511Z",
            "date_update": "2019-04-01T15:12:53.453569Z",
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
            "briefing": "The one hundred and forty-fifth best briefing ever",
            "ps": ""
        },
        {
            "id": 144,
            "name": "inverno 2020",
            "date_creation": "2019-11-21T19:43:21.862687Z",
            "date_update": null,
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
        "briefing": "The best briefing ever",
        "ps": ""
    }


POST
====

You need to do post request with the collection attributes in the body to create a new collection.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/collection/

body:

.. code-block:: bash

    {
        "name": "verão 2019",
        "date_update": "2018-12-20T15:50:25.843449Z",
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
        "ps": ""
    }


**Response:**

.. code-block:: bash

    {
        "id": 145,
        "name": "verão 2020",
        "date_creation": "2019-11-21T19:43:21.862687Z",
        "date_update": "2019-12-20T21:23:12.783479Z",
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
        "briefing": "The best briefing ever",
        "ps": ""
    }

P.S: The response will contains the new values.


------------------------

Color
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

   * - feedback
     - Feedback
     - true
     -

   * - image
     - file
     - true
     - jpeg

   * - psd_original
     - file
     - false
     - psd

   * - psd_final
     - file
     - false
     - psd

   * - psd_flirted
     - file
     - false
     - psd



GET
===

If you want to get all colors, use:

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/color/

**Response:**

.. code-block:: bash

    [
        {
            "id" : 1,
            "image": "color/small/1.jpg"
            "psd_original": null,
            "psd_final": null,
            "psd_flirted": null,
            "feedback": 4,
        },
        {
            "id" : 2,
            "image": "color/small/2.jpg"
            "psd_original": color/psd/original/2.psd,
            "psd_final": null,
            "psd_flirted": null,
            "feedback": 4,
        }
        ...
    ]

But if you prefer to take one color. Replace the <id> for the value that you want.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/color/<id>/

**Response:**

.. code-block:: bash

    {
        "id" : 1,
        "image": "color/small/1.jpg"
        "psd_original": null,
        "psd_final": null,
        "psd_flirted": null,
        "feedback": 4,
    }

POST
====

You need to do post request with the color attributes in the body to create a new color.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/color/

body:

.. code-block:: bash

    {
        "image": "color/small/1.jpg"
        "psd_original": null,
        "psd_final": null,
        "psd_flirted": null,
        "feedback": 4,
    }


**Response:**

.. code-block:: bash

    {
        "id" : 1,
        "image": "color/small/1.jpg"
        "psd_original": null,
        "psd_final": null,
        "psd_flirted": null,
        "feedback": 4,
    }

PUT
===

Choose the color that you want to update and replace the <id> to color ID and add all the attributes in the body.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/color/<id>/

body:

.. code-block:: bash

    {
        "image": "color/small/3.jpg"
        "psd_original": null,
        "psd_final": null,
        "psd_flirted": null,
        "feedback": 4,
    }


**Response:**

.. code-block:: bash

    {
        "id" : 1,
        "image": "color/small/3.jpg"
        "psd_original": null,
        "psd_final": null,
        "psd_flirted": null,
        "feedback": 4,
    }

P.S: The response will contains the new values.


PATCH
=====

Choose the color that you want to partial update and replace the <id> to color ID and add all the attributes in the body.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/color/<id>/

body:

.. code-block:: bash

    {
        "image": "color/small/3.jpg"
    }

**Response:**

.. code-block:: bash

    {
        "id" : 1,
        "image": "color/small/3.jpg"
        "psd_original": null,
        "psd_final": null,
        "psd_flirted": null,
        "feedback": 4,
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

If you want to get all feedbacks, use:

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

You need to do post request with the feedback attributes in the body to create a new collection.

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

   * - designer
     - User
     - true
     -
     -

   * - collection
     - Collection
     - false
     -
     -

   * - code
     - string
     - true
     -
     -

   * - exclusivity
     - string
     - true
     -
     - none, national, regional

   * - status
     - string
     - true
     -
     - approved, revision, denied, sketch

   * - type
     - string
     - true
     -
     - digital, cylinder

   * - date_creation *
     - datetime
     - true
     -
     -

   * - date_update *
     - datetime
     - true
     -
     -

   * - image
     - file
     - true
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

P.S.: The date_request and date_update are not required because the value default is the current time.

GET
===

If you want to get all print, use:

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
            "exclusivity": "none",
            "status": "sketch",
            "type": "digital",
            "date_creation": "2019-10-05T12:52:610239Z",
            "date_update": "2019-12-03T15:64:610239Z",
            "image": "print/small/L12345.jpg"
            "psd_original": "print/psd/original/L12345.psd",
            "psd_final": null,
            "psd_flirted": null,
            "designer": 1,
            "collection": 1
        },
        {
            "id": 2,
            "tagprint_set": [
                {
                    "tag": {
                        "id": 1,
                        "name": "aquarela",
                        "category": 1
                    }
                },
                    "tag": {
                        "id": 1,
                        "name": "bordados",
                        "category": 1
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
            "code": "L123456",
            "exclusivity": "national",
            "status": "approved",
            "type": "digital",
            "date_creation": "2019-11-05T10:31:112329Z",
            "date_update": "2019-12-05T12:22:530123Z",
            "image": "print/small/L123456.jpg"
            "psd_original": "print/psd/original/L123456.psd",
            "psd_final": "print/psd/final/L123456.psd",
            "psd_flirted": null,
            "designer": 1,
            "collection": 1
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
        "exclusivity": "none",
        "status": "sketch",
        "type": "digital",
        "date_creation": "2019-10-05T12:52:610239Z",
        "date_update": "2019-12-03T15:64:610239Z",
        "image": "print/small/L12345.jpg"
        "psd_original": "print/psd/original/L12345.jpg",
        "psd_final": null,
        "psd_flirted": null,
        "designer": 1,
        "collection": 1
    }


POST
====

You need to do post request with the print attributes in the body to create a new print.

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
        "exclusivity": "none",
        "status": "sketch",
        "type": "digital",
        "image": "print/small/L12345.jpg"
        "psd_original": "print/psd/original/L12345.psd",
        "psd_final": null,
        "psd_flirted": null,
        "designer": 1,
        "collection": 1
    }


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
        "exclusivity": "none",
        "status": "sketch",
        "type": "digital",
        "date_creation": "2019-10-05T12:52:610239Z",
        "date_update": null,
        "image": "print/small/L12345.jpg"
        "psd_original": "print/psd/original/L12345.psd",
        "psd_final": null,
        "psd_flirted": null,
        "designer": 1,
        "collection": 1
    }


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
        "exclusivity": "none",
        "status": "sketch",
        "type": "digital",
        "image": "print/small/L12345.jpg"
        "psd_original": "print/psd/original/L12345.psd",
        "psd_final": "print/psd/final/L12345.psd",
        "psd_flirted": null,
        "designer": 1,
        "collection": 1
    }


**Response:**

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
        "exclusivity": "none",
        "status": "revision",
        "type": "digital",
        "date_creation": "2019-10-05T12:52:610239Z",
        "date_update": "2019-12-03T15:64:610239Z",
        "image": "print/small/L12345.jpg"
        "psd_original": "print/psd/original/L12345.psd",
        "psd_final": "print/psd/final/L12345.psd",
        "psd_flirted": null,
        "designer": 1,
        "collection": 1
    }

P.S: The response will contains the new values.


PATCH
=====

Choose the print that you want to partial update and replace the <id> to reserve ID and add all the attributes in the body.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/print/<id>/

body:

.. code-block:: bash

    {
        "status": "revision",
        "psd_final": "print/psd/final/L12345.psd",
    }

**Response:**

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
        "exclusivity": "none",
        "status": "revision",
        "type": "digital",
        "date_creation": "2019-10-05T12:52:610239Z",
        "date_update": "2019-12-03T15:64:610239Z",
        "image": "print/small/L12345.jpg"
        "psd_original": "print/psd/original/L12345.psd",
        "psd_final": "print/psd/final/L12345.psd",
        "psd_flirted": null,
        "designer": 1,
        "collection": 1
    }

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
            "status": "revision",
            "exclusivity": "none",
            "collection": null,
            "type": "digital"
        },
        {
            "image": "/print/small/L12345.jpg"
            "code": "L12345",
            "status": "approved",
            "exclusivity": "national",
            "collection": 2,
            "type": "digital"
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

   * - clerk
     - User
     - true

   * - print
     - Print
     - true

   * - date_request *
     - datetime
     - false

   * - date_end
     - datetime
     - true

P.S.: The date_request is not required because the value default is the current time.


GET
===

If you want to get all reserve, use:

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

You need to do post request with the reserve attributes in the body to create a new reserve.

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

If you want to get all tags, use:

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

You need to do post request with the tag attributes in the body to create a new tag.

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


