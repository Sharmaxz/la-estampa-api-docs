La Estampa API
========================

Project develop in Python 3.7, Django 2.2.6 and Django Rest Framework 3.10.3 to provide REST API for La Estampa Website.

Requirements
~~~~~~~~~~~~~

- Python_ (3.7, 3.8)
- Django_ (2.2.6, 2.2.7)
- `Django Rest Framework`_ (3.10.3)

.. _Python: https://www.python.org/
.. _Django: https://www.djangoproject.com/
.. _Django Rest Framework: https://www.django-rest-framework.org/

Installation
~~~~~~~~~~~~
 We strongly recommended to use virtualenv, but if you are not familiar with virtualenv, you can read more in ''https://virtualenv.pypa.io/en/latest/''

.. code-block:: bash

   $ pip install -r requirements.txt

Environment Variables
~~~~~~~~~~~~~~~~~~~~~~
 We have to create a .env file in project root folder with this informations.
 If you don't have access to theses keys contact the development team.

.. code-block:: bash

    ALLOWED_HOSTS=''
    DATABASE_URL=''
    DEBUG=True
    SECRET_KEY=''


Run
~~~~~~~~~
Run the following command:

.. code-block:: bash

   $ python manage.py runserver

EndPoints
~~~~~~~~~~

Our architecture follow Representational State Transfer (REST) architectural style for for distributed hypermedia systems (API's).

.. toctree::
   :maxdepth: 1

   endpoints-dev
