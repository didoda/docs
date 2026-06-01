Project model ``/model/project``
================================

``/model/project`` endpoint returns a compact representation of the current project model.

This endpoint is useful when you need a single resource describing model configuration at project level.

Get project model
-----------------

You can retrieve project model information by invoking ``GET /model/project``.

.. http:get:: /model/project

**Example request (get project model)**:

.. sourcecode:: http

    GET /model/project HTTP/1.1
    Host: api.example.com
    Accept: application/json

Expected response is ``HTTP/1.1 200 OK`` with ``application/json`` body.
