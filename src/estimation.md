# Estimation (time and fees)

To provide users with a convenient solution, we've implemented an endpoint designed to offer estimations for both time and fees. This allows users to gauge potential costs and delivery times without the need to initiate the order creation process.


To try the estimation, you will need to make an HTTP POST request to the following endpoint:

```
http://api.armadadelivery.com/v0/deliveries/estimate`
```

> For the sandbox environment please use the following domain name: `https://9vxtmhgzrr.eu-west-1.awsapprunner.com`

The body of the request should be in JSON format and include the following parameters:

* `branch`: The branch ID, Start point (Required).
* `destination`: The final customer destination (Required):
    - `latitude`: (Required). 
    - `longitude`: (Required).

Example request:

```bash
curl --location --request POST 'https://api.armadadelivery.com/v0/deliveries/estimate' \
--header 'Authorization: Key YOUR API KEY' \
--header 'Content-Type: application/json' \
--data-raw '{
    "branch": "5eef2043bfa02f001c17b229",
    "destination": {
        "latitude": 29.3300,
        "longitude": 47.9085,
    }
}'
```

RESPONSE SCHEMA:
```js
{
	deliveryFee: Number,
	pickupEta: ISODATE,
	deliveryEta: ISODATE,
}
```

* `deliveryFee`: The trip cost.
* `pickupEta`: Expected date and time for driver pickup. _(Eta: Estimated Arrival time)_
* `deliveryEta`: Expected date and time of arrival for the driver. _(Eta: Estimated Arrival time)_

Example response:
```js
{
	deliveryFee: 17,
	pickupEta: 2024-01-18T14:48:00.000Z,
	deliveryEta: 2024-01-18T15:39:00.000Z,,
}
```
