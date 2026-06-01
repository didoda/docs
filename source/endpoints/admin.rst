Administration ``/admin``
==========================

``/admin`` endpoint deals with administrative operations on current project.

Managed resources by this endpoint are:

* applications
* auth providers
* asynchronous jobs
* configuration properties
* custom endpoints
* external auth links

Each managed resource follows the same CRUD pattern:

* ``POST /admin/{resource}`` create resource
* ``GET /admin/{resource}`` list resources
* ``GET /admin/{resource}/{id}`` get single resource
* ``PATCH /admin/{resource}/{id}`` modify resource
* ``DELETE /admin/{resource}/{id}`` remove resource

Applications
------------

Applications are managed through ``/admin/applications``.

Available operations are:

* ``POST /admin/applications``
* ``GET /admin/applications``
* ``GET /admin/applications/{id}``
* ``PATCH /admin/applications/{id}``
* ``DELETE /admin/applications/{id}``

**Example request: create application**:

.. sourcecode:: http

    POST /admin/applications HTTP/1.1
    Host: api.example.com
    Accept: application/vnd.api+json
    Content-Type: application/vnd.api+json

    {
        "data": {
            "type": "applications",
            "attributes": {
                "name": "my-very-first-app",
                "description": "My first app"
            }
        }
    }

Auth Providers
--------------

Auth providers are managed through ``/admin/auth_providers``.

Available operations are:

* ``POST /admin/auth_providers``
* ``GET /admin/auth_providers``
* ``GET /admin/auth_providers/{id}``
* ``PATCH /admin/auth_providers/{id}``
* ``DELETE /admin/auth_providers/{id}``

**Example request: create auth provider**:

.. sourcecode:: http

    POST /admin/auth_providers HTTP/1.1
    Host: api.example.com
    Accept: application/vnd.api+json
    Content-Type: application/vnd.api+json

    {
        "data": {
            "type": "auth_providers",
            "attributes": {
                "name": "my-provider"
            }
        }
    }

Async Jobs
----------

Asynchronous jobs are managed through ``/admin/async_jobs``.

Available operations are:

* ``POST /admin/async_jobs``
* ``GET /admin/async_jobs``
* ``GET /admin/async_jobs/{id}``
* ``PATCH /admin/async_jobs/{id}``
* ``DELETE /admin/async_jobs/{id}``

**Example request: create async job**:

.. sourcecode:: http

    POST /admin/async_jobs HTTP/1.1
    Host: api.example.com
    Accept: application/vnd.api+json
    Content-Type: application/vnd.api+json

    {
        "data": {
            "type": "async_jobs",
            "attributes": {
                "service": "dummy"
            }
        }
    }

Configuration
-------------

Configuration properties are managed through ``/admin/config``.

Available operations are:

* ``POST /admin/config``
* ``GET /admin/config``
* ``GET /admin/config/{id}``
* ``PATCH /admin/config/{id}``
* ``DELETE /admin/config/{id}``

**Example request: create config**:

.. sourcecode:: http

    POST /admin/config HTTP/1.1
    Host: api.example.com
    Accept: application/vnd.api+json
    Content-Type: application/json

    {
        "data": {
            "id": "TestConf",
            "type": "config",
            "attributes": {
                "name": "TestConf",
                "content": "config content",
                "context": "config-context"
            }
        }
    }

Endpoints
---------

Custom endpoints are managed through ``/admin/endpoints``.

Available operations are:

* ``POST /admin/endpoints``
* ``GET /admin/endpoints``
* ``GET /admin/endpoints/{id}``
* ``PATCH /admin/endpoints/{id}``
* ``DELETE /admin/endpoints/{id}``

**Example request: create endpoint**:

.. sourcecode:: http

    POST /admin/endpoints HTTP/1.1
    Host: api.example.com
    Accept: application/vnd.api+json
    Content-Type: application/vnd.api+json

    {
        "data": {
            "type": "endpoints",
            "attributes": {
                "name": "my_endpoint",
                "description": "My first endpoint"
            }
        }
    }

External Auth
-------------

External auth mappings are managed through ``/admin/external_auth``.

Available operations are:

* ``POST /admin/external_auth``
* ``GET /admin/external_auth``
* ``GET /admin/external_auth/{id}``
* ``PATCH /admin/external_auth/{id}``
* ``DELETE /admin/external_auth/{id}``

**Example request: create external auth mapping**:

.. sourcecode:: http

    POST /admin/external_auth HTTP/1.1
    Host: api.example.com
    Accept: application/vnd.api+json
    Content-Type: application/vnd.api+json

    {
        "data": {
            "type": "external_auth",
            "attributes": {
                "user_id": 1,
                "auth_provider_id": 1,
                "provider_username": "id"
            }
        }
    }

Response codes
--------------

For all admin resources, expected responses are:

* ``201 Created`` for successful creation
* ``200 OK`` for list/get/modify operations
* ``204 No Content`` for delete operations
* ``404 Not Found`` for missing resources

