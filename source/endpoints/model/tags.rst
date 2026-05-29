Tags ``/model/tags``
====================

``/model/tags`` endpoint manages tags for object types.

Tags are associated to object types and can be used to classify objects and filter resources, for instance through ``filter[tags]`` on object endpoints.

With this endpoint you can:

* create, update and remove tags
* get a single tag
* list tags
* retrieve object tags linked to a tag

Create a tag
------------

Creation of a new tag happens through ``POST /model/tags`` endpoint.

.. http:post:: /model/tags

**Example request: create tag**:

.. sourcecode:: http

    POST /model/tags HTTP/1.1
    Host: api.example.com
    Accept: application/vnd.api+json
    Content-Type: application/json

    {
        "data": {
            "type": "tags",
            "attributes": {
                "name": "test-tag",
                "label": "Test Tag"
            }
        }
    }

Main attributes used on tag creation are:

* ``name`` tag name in lowered `snake_case <https://en.wikipedia.org/wiki/Snake_case>`_ format
* ``label`` display label

Expected response is ``HTTP/1.1 201 Created``, with ``application/vnd.api+json`` body data representing tag just created.

If tag already exists or input data is not valid, POST fails and response will be ``400 Bad Request - Invalid data``.

Get a single tag
----------------

You can obtain a single tag by invoking ``GET /model/tags/{tagId}``.

.. http:get:: /model/tags/{tagId}

* ``{tagId}`` is the tag identifier

**Example request (get tag)**:

.. sourcecode:: http

    GET /model/tags/1 HTTP/1.1
    Host: api.example.com
    Accept: application/vnd.api+json

Expected response is ``HTTP/1.1 200 OK``.

If tag is not found, response will be ``404 Not Found``.

Get object tags
---------------

To retrieve object tags linked to a tag invoke ``GET /model/tags/{tagId}/object_tags``.

.. http:get:: /model/tags/{tagId}/object_tags

* ``{tagId}`` is the tag identifier

**Example request (get object tags)**:

.. sourcecode:: http

    GET /model/tags/1/object_tags HTTP/1.1
    Host: api.example.com
    Accept: application/vnd.api+json

Expected response is ``HTTP/1.1 200 OK`` with a list in ``"data"``.

Tags list
---------

To retrieve a list of tags you can invoke ``GET /model/tags`` and use common filters like :ref:`filter-field` or :ref:`filter-search`.

.. http:get:: /model/tags

**Example request: get tags**:

.. sourcecode:: http

    GET /model/tags HTTP/1.1
    Accept: application/vnd.api+json

Response will contain an array of ``tags`` in typical list format as shown in :ref:`api-responses`.

Modify a tag
------------

You can modify a tag by using ``PATCH /model/tags/{tagId}`` endpoint.

.. http:patch:: /model/tags/{tagId}

* ``{tagId}`` is the tag identifier

**Example request: modify tag**:

.. sourcecode:: http

    PATCH /model/tags/1 HTTP/1.1
    Host: api.example.com
    Accept: application/vnd.api+json
    Content-Type: application/json

    {
        "data": {
            "id": "1",
            "type": "tags",
            "attributes": {
                "label": "Nice tag"
            }
        }
    }

Expected response is ``HTTP/1.1 200 OK``.

Remove a tag
------------

You can delete a tag permanently by using ``DELETE /model/tags/{tagId}`` endpoint.

.. http:delete:: /model/tags/{tagId}

* ``{tagId}`` is the tag identifier

**Example request: delete tag**:

.. sourcecode:: http

    DELETE /model/tags/1 HTTP/1.1
    Host: api.example.com
    Accept: application/vnd.api+json

Expected HTTP status response is ``204 No Content``.

If tag is not found, response will be ``404 Not Found``.
