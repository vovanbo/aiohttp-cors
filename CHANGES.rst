CHANGES
=======

0.5.0 (2016-XX-XX)
------------------


0.4.0 (2016-04-04)
------------------

- Fixed support with new Resources objects introduced in ``aiohttp`` 0.21.0.
  Minimum supported version of ``aiohttp`` is 0.21.4 now.

- New Resources objects are supported.
  You can specify default configuration for a Resource and use
  ``allow_methods`` to explicitly list allowed methods (or ``*`` for all
  HTTP methods):

  .. code-block:: python

        # Allow POST and PUT requests from "http://client.example.org" origin.
        hello_resource = cors.add(app.router.add_resource("/hello"), {
                "http://client.example.org":
                    aiohttp_cors.ResourceOptions(
                        allow_methods=["POST", "PUT"]),
            })
        # No need to add POST and PUT routes into CORS configuration object.
        hello_resource.add_route("POST", handler_post)
        hello_resource.add_route("PUT", handler_put)
        # Still you can add additional methods to CORS configuration object:
        cors.add(hello_resource.add_route("DELETE", handler_delete))

- ``AbstractRouterAdapter`` was completely rewritten to be more Router
  agnostic.

0.3.0 (2016-02-06)
------------------

- Rename ``UrlDistatcherRouterAdapter`` to ``UrlDispatcherRouterAdapter``.

- Set maximum supported ``aiohttp`` version to ``0.20.2``, see bug #30 for
  details.

0.2.0 (2015-11-30)
------------------

- Move ABCs from ``aiohttp_cors.router_adapter`` to ``aiohttp_cors.abc``.

- Rename ``RouterAdapter`` to ``AbstractRouterAdapter``.

- Fix bug with configuring CORS for named routes.

0.1.0 (2015-11-05)
------------------

* Initial release.
