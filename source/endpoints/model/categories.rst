Categories ``/model/categories``
================================

``/model/categories`` endpoint manages categories for object types.

Categories are associated to object types and can be used to classify objects and filter resources, for instance through ``filter[categories]`` on object endpoints.

With this endpoint you can:

* create, update and remove categories
* get a single category
* list categories
* retrieve object categories linked to a category

.. _api-model-categories:

Create a category
-----------------

Creation of a new category happens through ``POST /model/categories`` endpoint.

.. http:post:: /model/categories

**Example request: create category**:

.. sourcecode:: http

	POST /model/categories HTTP/1.1
	Host: api.example.com
	Accept: application/vnd.api+json
	Content-Type: application/json

	{
		"data": {
			"type": "categories",
			"attributes": {
				"name": "new-name",
				"label": "New Label",
				"object_type_name": "events"
			}
		}
	}

Main attributes used on category creation are:

* ``name`` category name in lowered `snake_case <https://en.wikipedia.org/wiki/Snake_case>`_ format
* ``label`` display label
* ``object_type_name`` object type associated with this category

Expected response is ``HTTP/1.1 201 Created``, with ``application/vnd.api+json`` body data representing category just created.

If category already exists or input data is not valid, POST fails and response will be ``400 Bad Request - Invalid data``.

Get a single category
---------------------

You can obtain a single category by invoking ``GET /model/categories/{categoryId}``.

.. http:get:: /model/categories/{categoryId}

* ``{categoryId}`` is the category identifier

**Example request (get category)**:

.. sourcecode:: http

	GET /model/categories/1 HTTP/1.1
	Host: api.example.com
	Accept: application/vnd.api+json

Expected response is ``HTTP/1.1 200 OK``.

If category is not found, response will be ``404 Not Found``.

Get object categories
---------------------

To retrieve object categories linked to a category invoke ``GET /model/categories/{categoryId}/object_categories``.

.. http:get:: /model/categories/{categoryId}/object_categories

* ``{categoryId}`` is the category identifier

**Example request (get object categories)**:

.. sourcecode:: http

	GET /model/categories/1/object_categories HTTP/1.1
	Host: api.example.com
	Accept: application/vnd.api+json

Expected response is ``HTTP/1.1 200 OK`` with a list in ``"data"``.

Categories list
---------------

To retrieve a list of categories you can invoke ``GET /model/categories`` and use common filters like :ref:`filter-field` or :ref:`filter-search`.

.. http:get:: /model/categories

**Example request: get categories**:

.. sourcecode:: http

	GET /model/categories HTTP/1.1
	Accept: application/vnd.api+json

Response will contain an array of ``categories`` in typical list format as shown in :ref:`api-responses`.

You can filter by object type using ``filter[type]``.

**Example request: get categories by type**:

.. sourcecode:: http

	GET /model/categories?filter[type]=events HTTP/1.1
	Accept: application/vnd.api+json

Modify a category
-----------------

You can modify a category by using ``PATCH /model/categories/{categoryId}`` endpoint.

.. http:patch:: /model/categories/{categoryId}

* ``{categoryId}`` is the category identifier

**Example request: disable category**:

.. sourcecode:: http

	PATCH /model/categories/1 HTTP/1.1
	Host: api.example.com
	Accept: application/vnd.api+json
	Content-Type: application/json

	{
		"data": {
			"id": "1",
			"type": "categories",
			"attributes": {
				"enabled": false
			}
		}
	}

**Example request: change label**:

.. sourcecode:: http

	PATCH /model/categories/1 HTTP/1.1
	Host: api.example.com
	Accept: application/vnd.api+json
	Content-Type: application/json

	{
		"data": {
			"id": "1",
			"type": "categories",
			"attributes": {
				"label": "nice category!"
			}
		}
	}

Expected response is ``HTTP/1.1 200 OK``.

Remove a category
-----------------

You can delete a category permanently by using ``DELETE /model/categories/{categoryId}`` endpoint.

.. http:delete:: /model/categories/{categoryId}

* ``{categoryId}`` is the category identifier

**Example request: delete category**:

.. sourcecode:: http

	DELETE /model/categories/1 HTTP/1.1
	Host: api.example.com
	Accept: application/vnd.api+json

Expected HTTP status response is ``204 No Content``.

If category is not found, response will be ``404 Not Found``.
