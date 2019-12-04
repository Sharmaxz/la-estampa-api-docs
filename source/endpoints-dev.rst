Authenticating Requests
-----------------------

All endpoints requires authentication.

PLEASE WRITE ME


------------------------

Briefing
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

   * - images
     - FileField
     - false

   * - print
     - Print
     - true


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
            "date_creation": "2018-12-21",
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

The color

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

   * - image
     - integer
     - true
     - jpeg

   * - psd_original
     - integer
     - true
     - psd

   * - psd_final
     - datetime
     - false
     - psd

   * - psd_flirted
     - datetime
     - false
     - psd

   * - feedback
     - string
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

        },
        {

        }
        ...
    ]

But if you prefer to take one category. Replace the <id> for the value that you want.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/color/<id>/

**Response:**

.. code-block:: bash

    {

    }

POST
====

You need to do post request with the color attributes in the body to create a new color.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/color/

body:

.. code-block:: bash

    {

    }


**Response:**

.. code-block:: bash

    {

    }


PUT
===

Choose the color that you want to update and replace the <id> to color ID and add all the attributes in the body.

.. code-block:: bash

    https://la-estampa.herokuapp.com/api/color/<id>/

body:

.. code-block:: bash

    {

    }


**Response:**

.. code-block:: bash

    {

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

    }

**Response:**

.. code-block:: bash

    {

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
            "date": "2019-13-03T13:03:30.601202Z",
            "text": "Yes, I knew it. I warned you",
            "data": {},
            "print": 1,
            "sender": 1
        },
        {
            "id": 23,
            "date": "2019-13-03T12:46:24.502605Z",
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
        "date": "2019-13-03T13:05:30.601202Z",
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
        "date": "2019-13-03T13:05:30.601202Z",
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
        "date": "2019-13-03T13:05:30.601202Z",
        "text": "Ok, I will change to blue. I hope this looks cool.",
        "data": {},
        "print": 1,
        "sender": 2
    }

P.S: The response will contains the new values.

------------------------

Reserve
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


