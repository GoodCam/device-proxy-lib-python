# Changelog

## v0.1.10 (2024-02-14)

* Update the native library
* Fix response header construction

## v0.1.9 (2023-08-21)

* Add certificate renew timeout for Let's Encrypt
* Mitigate possible slowloris attacks

## v0.1.8 (2023-08-14)

* Lower the memory footprint

## v0.1.7 (2023-08-10)

* Fix poll after error in the native lib

## v0.1.6 (2023-01-23)

* Add missing Connection and Upgrade headers in responses to HTTP/1.1
  connection upgrades

## v0.1.5 (2023-01-11)

* Do not forward hop-by-hop and non-http2 headers to the device and fix
  connection upgrades

## v0.1.4 (2023-01-09)

* Allow constructing responses with body and headers as `__init__` arguments
* Improve logging in situations when a device is registered but forwarding a
  client request fails for some reason

## v0.1.3 (2022-11-13)

* Fix invalid memory access when reading data from the Authorization object
  within an asynchronous request handler

## v0.1.2 (2022-11-24)

* Detect broken device connections

## v0.1.1 (2022-11-23)

* Updated dependency

## v0.1.0 (2022-11-23)

* Initial release
