Creating a Delivery
===================
A delivery is defined as the shipping of goods from one point of origin to one customer. In rare cases, it also includes the return trip if customer returns or rejects the goods.

Types of Deliveries
-------------------

                | Goods stored at | Delivery initiated by     | Tracking number
----------------|-----------------|---------------------------|-------------------------------
**Fulfillment** | Provider        | Sending order to provider | Provider generated through API
**Pickup**      | Merchant        | Sending order to provider | Provider generated through API
**Shipment**    | Merchant        | Dropping off at provider  | Merchant entered manually

A **fulfillment** service provider typically stores goods from multiple merchants in a single warehouse. When a delivery order is created, a human staff or a machine prepares the goods for delivery, and sends it off through a logistical channel.

A **pickup** service provider receives an incoming delivery order and dispatches an appropriate delivery unit e.g. a van or a motorcycle to merchant's warehouse. Merchant is normally responsible for preparing the package for pickup at an agreed upon time, and the provider ensures that the package is delivered to the final destination.

A **shipment** provider is the only type of provider whose workflow can be completed entirely offline. After merchant drops off the goods at their designated stations, they generate a tracking number which merchant can use to track the progress. For a sales platform to be notified of tracking updates, they need to explicitly register the desired tracking number with the provider.

Protocol
--------
TBC
