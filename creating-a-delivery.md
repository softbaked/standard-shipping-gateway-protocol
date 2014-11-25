Creating a Delivery
===================
A delivery is defined as the shipping of goods by the shipping gateway, from the point of origin to a single customer. In rare cases, it also includes the return trip if customer returns or rejects the goods.

Types of Shipping Gateways
--------------------------

                | Goods stored at | Delivery initiated by     | Tracking number
----------------|-----------------|---------------------------|-------------------------------
**Fulfillment** | Provider        | Sending order to provider | Provider generated through API
**Pickup**      | Merchant        | Sending order to provider | Provider generated through API
**Shipment**    | Merchant        | Dropping off at provider  | Merchant entered manually

A *fulfillment service provider* typically stores goods from multiple merchants in a single warehouse. When a delivery order is created, a human staff or a machine prepares the goods for delivery, and sends it off through a logistical channel.

A *pickup service provider* receives an incoming delivery order and dispatches an appropriate delivery unit e.g. a van or a motorcycle to merchant's warehouse. Merchant is normally responsible for preparing the package for pickup at an agreed upon time, and the provider ensures that the package is delivered to the final destination.

A *shipment provider* is the only type of provider whose workflow can be completed entirely offline. After merchant drops off the goods at their designated stations, they generate a tracking number which merchant can use to track the progress. For a sales platform to be notified of tracking updates, they need to explicitly register the desired tracking number with the provider.

When the distinction between these types of providers are not important, they are simply referred to as the *shipping gateway*.

Protocol
--------
To create a delivery, the *sales platform* issues a HTTPS POST command to the *shipping gateway*'s HTTPS server, at the agreed upon endpoint that is unique to each merchant. Note that this implies that the merchant has to be registered in both services.

The following HTTPS POST parameters must be provided, using any valid means of embedding parameters (`x-www-form-urlencoded`, `multipart/form-data`, etc.):

- **`order_id`** (REQUIRED): a string that uniquely identifies the order that causes the shipment to exist in the first place. The shipping gateway MUST NOT assume a 1:1 relationship between an order and a shipment, nor assume that any of the shipping parameters such as recipient address and item list will be consistent across different shipments sharing the same `order_id`.
- **`customer[name]`** (REQUIRED): a one-line string bearing the title of the shipment's recipient.
- **`customer[address]`** (REQUIRED): a multi-line text of a valid postal address at which the shipment is meant to be delivered. Country MAY be omitted if the address is inside the *shipping gateway*'s base country. Future versions of the specification MAY require semantically formatted addresses. Delivery directions SHOULD NOT be included here but instead in the `note` field.
- **`customer[phone]`** (RECOMMENDED): a valid phone number where the recipient may be reached to confirm or authorize a delivery. Country code SHOULD be omitted unless the recipient is outside of the *shipping gateway*'s base country. The semantical correctness of this field is not validated, and occasionally it may include instructions or extension codes in non-machine-readable format.
- **`callback`** (RECOMMENDED): a valid HTTPS endpoint where the *sales platform* expects to be notified about updates on this delivery. More information about this under [Tracking a delivery](tracking-a-delivery).

All parameters MUST be encoded in UTF-8 and subsequently encoded as required by HTTP, e.g. urlencoded.
