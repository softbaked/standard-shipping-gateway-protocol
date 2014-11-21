Standard Shipping Gateway Protocol
==================================
This document specifies the Standard Shipping Gateway Protocol which defines computerized transactional messages between online sales platforms and shipping gateways.

Status
------
This document is in initial development and the specification should not be considered stable. The version number is 0.1.0.

Licensing
---------
The specifications here may be adopted by any party interested in ease of integration with other platforms for free of charge. For more information, please see [License](/LICENSE).

Introduction
------------
The rapidly growing ecommerce ecosystem has given birth to numerous platforms and services with complementary functions. While it is in most party's best interest to integrate with as many other providers as possible, the technical cost of each integration can be forbidding for small companies.

In the interest of promoting cooperation and integration between these small providers, we propose Standard Shipping Gateway Protocol, a set of technical specifications which define how online sales platforms may communicate to shipping gateways and vice versa to create and track shipments. These specifications take into account how most commercial sales platforms and shipping gateways already operate. Properly implemented, they should allow for one-click interoperatability without having to tailor your software specifically for any vendor.

The protocol is built on HTTP and generally tries to be RESTful where possible.

If you would like to contribute to the development, please open an issue or a pull request on GitHub.

Table of Contents
-----------------
- [Creating a delivery](/creating-a-delivery.md)
- [Tracking a delivery](/tracking-a-delivery.md)

Sponsors
--------
- [Page365](http://get.page365.net)
