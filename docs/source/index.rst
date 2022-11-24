.. include:: ../../README.md
   :parser: myst_parser.sphinx_

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
