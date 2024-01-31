> The merchant creation should be requested from our operations team!

## Create Branch

To create a branch, you will need to make an HTTP POST request to the following endpoint:

```
http://api.armadadelivery.com/v0/branches
```

> To test your work on the sandbox or staging API, please refer to the [Testing Environments ](/sandbox_access) section for detailed instructions.

The body of the request should be in JSON format and include the following parameters:

* `name`: Branch name, Between 2 and 40 (String - Required).
* `phone`: Branch phone number (String - Required).
* `address`: The branch address (Object Required):
    - `locations`: Geo-Locations address (Object Required):
        - `latitude`: (Float Required). 
        - `longitude`: (Float Required).
    - `firstLine`: A Complete Regular Address, It’s important for drivers as a human readable address (String - Optional).

> Note 💡

> If you don't specify a `firstLine`, We will create it using the nearest location in our databases. However, keep in mind that the automatically generated address may not be entirely accurate. For better precision, consider providing specific details whenever possible.

Example request:

```bash
curl --location --request POST 'https://api.armadadelivery.com/v0/branches' \
--header 'Authorization: Key [YOUR API KEY]' \
--header 'Content-Type: application/json' \
--data-raw '{
    "name": "NAQSH",
    "phone": "+96500000000",
    "address": {
        "location":{
	        "latitude": 29.192375,
	        "longitude": 48.111894,
	},
        "firstLine": "Abu Hassaniah, Block 10, St 60, 36B",
    },
}'
```

The response will include the details from your request body, along with the `_id` and `apiKey` associated with the branch.

RESPONSE SCHEMA:
```
{
	_id: string,
	address: {
	  locations:{
		  latitude: <branch_latitude>,
		  longitude: <branch_longitude>,
	  },
	  firstLine: string
	},
	phone: string,
	name: string
	apiKey: string
}
```

## Get All Branches

To get all branches, you will need to make an HTTP GET request to the following endpoint:

```
http://api.armadadelivery.com/v0/branches
```

Example request:

```bash
curl --location --request GET 'https://api.armadadelivery.com/v0/branches' \
--header 'Authorization: Key [YOUR API KEY]'
```

You will get an array of data.

RESPONSE SCHEMA:
```
[{
	_id: string,
	address: {
	  locations:{
		  latitude: <branch_latitude>,
		  longitude: <branch_longitude>,
	  },
	  firstLine: string
	},
	phone: string,
	name: string
	apiKey: string
}]
```

## Get One Branch

To get one branch, you will need to make an HTTP GET request to the following endpoint:

```
http://api.armadadelivery.com/v0/branches/:id
```

The `id` param is required.

Example request:

```bash
curl --location --request GET 'https://api.armadadelivery.com/v0/branches/5eef2043bfa02f001c17b229' \
--header 'Authorization: Key [YOUR API KEY]'
```

RESPONSE SCHEMA:
```
{
	_id: string,
	address: {
	  locations:{
		  latitude: <branch_latitude>,
		  longitude: <branch_longitude>,
	  },
	  firstLine: string
	},
	phone: string,
	name: string
	apiKey: string
}
```

## Update Branch

To update a branch, you will need to make an HTTP PUT request to the following endpoint:

```
http://api.armadadelivery.com/v0/branches/:id
```

The `id` param is required.

The body of the request should be in JSON format and include one of the following parameters:

* `name`: Branch name, Between 2 and 40 (String - Optional).
* `phone`: Branch phone number (String - Optional).
* `address`: The branch address (Object Optional):
    - `locations`: Geo-Locations address (Object Optional):
        - `latitude`: (Float Required). 
        - `longitude`: (Float Required).
    - `firstLine`: A Complete Regular Address, It’s important for drivers as a human readable address (String - Optional).

Example request:

```bash
curl --location --request PUT 'https://api.armadadelivery.com/v0/branches/5eef2043bfa02f001c17b229' \
--header 'Authorization: Key [YOUR API KEY]' \
--header 'Content-Type: application/json' \
--data-raw '{
    "name": "Alhambra Grill",
}'
```

RESPONSE SCHEMA:
```
{
	_id: string,
	address: {
	  locations:{
		  latitude: <branch_latitude>,
		  longitude: <branch_longitude>,
	  },
	  firstLine: string
	},
	phone: string,
	name: string
	apiKey: string
}
```

## Delete Branch

To delete a branch, you will need to make an HTTP DELETE request to the following endpoint:

```
http://api.armadadelivery.com/v0/branches/:id
```

The `id` param is required.

If successful, expect a response with HTTP `status` code `204`.

Example request:

```bash
curl --location --request DELETE 'https://api.armadadelivery.com/v0/branches/5eef2043bfa02f001c17b229' \
--header 'Authorization: Key [YOUR API KEY]'
```
