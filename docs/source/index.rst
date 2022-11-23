GoodCam Device Proxy
====================

This library simplifies creating HTTP proxies that can be used to communicate
with GoodCam devices in various networks. GoodCam devices contain a
`built-in client <https://goodcam.github.io/goodcam-api/#tag/cloud>`_ that can
be configured to connect automatically to a given proxy. Once connected, the
devices will wait for incoming HTTP requests. The proxy simply forwards
incoming HTTP requests to the connected devices.

Installation
------------

This library is just a wrapper over
`the Rust version <https://github.com/GoodCam/device-proxy-lib>`_ of the same
library. You can install this library using pip::

   pip install gcdevproxy

If there is no binary wheel available, pip will try to build also the
underlying Rust library. You will need the Rust compiler installed on your
system to do this. You can install it easily using::

   curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

See https://www.rust-lang.org/tools/install for more information.

Even though the Rust version of this library can be built for any platform
supported by Rust, this Python wrapper is currently available only for Linux
systems.

Usage example
-------------

The library supports both blocking and asynchronous API, though the
asynchronous API should be preferred due to a better performance. To use the
asynchronous API, simply use the ``create_proxy`` and ``RequestHandler``
equivalents from the ``gcdevproxy.aio`` module.

Please keep in mind that **when using the blocking API, your request handler
MUST be thread-safe!** The proxy runtime may call your handler from multiple
threads at the same time. You don't have to worry about this when using the
asynchronous API because your handler will be called only from the thread
running the Python's asyncio event loop (usually the main thread).

Asynchronous API
^^^^^^^^^^^^^^^^

::

   from gcdevproxy.aio import RequestHandler

   ...

   class MyRequestHandler(RequestHandler):
      async def handle_device_request(self, authorization: Authorization) -> 'DeviceHandlerResult':
         ...

      async def handle_client_request(self, request: Request) -> 'ClientHandlerResult':
         ...

   async def main():
      config = ProxyConfig()
      config.http_bindings = [('0.0.0.0', 8080)]
      config.request_handler = MyRequestHandler()

      proxy = await gcdevproxy.aio.create_proxy(config)

      await proxy.run()

   if __name__ == '__main__':
      asyncio.run(main())

Blocking API
^^^^^^^^^^^^

::

   from gcdevproxy import RequestHandler

   ...

   class MyRequestHandler(RequestHandler):
      def handle_device_request(self, authorization: Authorization) -> 'DeviceHandlerResult':
         ...

      def handle_client_request(self, request: Request) -> 'ClientHandlerResult':
         ...

   def main():
      config = ProxyConfig()
      config.http_bindings = [('0.0.0.0', 8080)]
      config.request_handler = MyRequestHandler()

      proxy = gcdevproxy.create_proxy(config)

      proxy.run()

   if __name__ == '__main__':
      main()


More examples
^^^^^^^^^^^^^

See the ``python/examples`` folder in the root of this repository for
ready-to-use examples.

Reference documentation
=======================

.. toctree::
   :maxdepth: 2
   :caption: Contents:

.. autofunction:: gcdevproxy.create_proxy

.. autofunction:: gcdevproxy.aio.create_proxy

.. autoclass:: gcdevproxy.ProxyConfig
   :members: __init__
   :special-members:

.. autoclass:: gcdevproxy.RequestHandler
   :members: handle_device_request, handle_client_request
   :special-members:

.. autoclass:: gcdevproxy.aio.RequestHandler
   :members: handle_device_request, handle_client_request
   :special-members:

.. autoclass:: gcdevproxy.Proxy
   :members: run, stop
   :special-members:

.. autoclass:: gcdevproxy.aio.Proxy
   :members: run, stop
   :special-members:

.. autoclass:: gcdevproxy.Authorization
   :members: device_id, device_key
   :special-members:

.. autoclass:: gcdevproxy.Request
   :members: get_header_value
   :special-members:

.. autoclass:: gcdevproxy.Response
   :members: __init__, append_header, set_header
   :special-members:

.. autoclass:: gcdevproxy.DeviceHandlerResult
   :special-members:

.. autoclass:: gcdevproxy.AcceptDevice
   :special-members:

.. autoclass:: gcdevproxy.UnauthorizedDevice
   :special-members:

.. autoclass:: gcdevproxy.RedirectDevice
   :members: __init__
   :special-members:

.. autoclass:: gcdevproxy.ClientHandlerResult
   :special-members:

.. autoclass:: gcdevproxy.ForwardRequest
   :members: __init__
   :special-members:

.. autoclass:: gcdevproxy.BlockRequest
   :members: __init__
   :special-members:

Indices and tables
==================

* :ref:`genindex`
