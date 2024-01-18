> The merchant creation should be requested from our operations team!

## Create Branch

To create a branch, you will need to make an HTTP POST request to the following endpoint:

```
http://api.armadadelivery.com/v0/branches
```

> For the sandbox environment please use the following domain name: `https://9vxtmhgzrr.eu-west-1.awsapprunner.com`

The body of the request should be in JSON format and include the following parameters:

* `name`: The branch name, Between 2 and 40 (Required).
* `phone`: The branch phone (Required).
* `address`: The branch address (Required):
    - `latitude`: (Required). 
    - `longitude`: (Required).

Example request:

```bash
curl --location --request POST 'https://api.armadadelivery.com/v0/branches' \
--header 'Authorization: Key YOUR API KEY' \
--header 'Content-Type: application/json' \
--data-raw '{
    "name": "Arabian Flavors",
    "phone": "+96555551234",
    "address": {
        "latitude": 29.3759,
        "longitude": 47.9774,
    }
}'
```

The response will include the details from your request body, along with the `_id` and `apiKey` associated with the branch.

RESPONSE SCHEMA:
```
{
	_id: string,
	address: {
		latitude: <branch_latitude>,
		longitude: <branch_longitude>,
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
--header 'Authorization: Key YOUR API KEY'
```

You will get an array of data.

RESPONSE SCHEMA:
```
[{
	_id: string,
	address: {
		latitude: <branch_latitude>,
		longitude: <branch_longitude>,
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
--header 'Authorization: Key YOUR API KEY'
```

RESPONSE SCHEMA:
```
{
	_id: string,
	address: {
		latitude: <branch_latitude>,
		longitude: <branch_longitude>,
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

* `name`: The branch name, Between 2 and 40 (Optional).
* `phone`: The branch phone (Optional).
* `address`: The branch address (Optional):
    - `latitude`: (Required for address change). 
    - `longitude`: (Required for address change).

Example request:

```bash
curl --location --request PUT 'https://api.armadadelivery.com/v0/branches/5eef2043bfa02f001c17b229' \
--header 'Authorization: Key YOUR API KEY' \
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
		latitude: <branch_latitude>,
		longitude: <branch_longitude>,
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
--header 'Authorization: Key YOUR API KEY'
```
