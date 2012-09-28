# Estimates
An estimate is a

## Get estimates
`GET /estimates.json` will return all your estimates.
```json
[
  {  
    "id":"50603e722f412e0435000024",
	"number":"0000003",
	"issue_date":"2012-09-24",
	"contact":{
	  "id":"5059bdbf2f412e0901000024",
	  "full_name":"Wild E. Coyote"
	},
	"po_number":"",
	"currency":"EUR",
	"items":[
	  {
        "description":"ACME TNT",
		"quantity":"1.0",
		"unit_price":"100.0",
		"discount_rate":"0.0",
		"tax_1_name":"",
		"tax_1_rate":"",
		"tax_2_name":"",
		"tax_2_rate":"",
		"subtotal":"\u20ac0.00",
		"discount":"\u20ac0.00",
		"gross_amount":"\u20ac0.00"
	   }
    ],
	"subtotal":"\u20ac0.00",
	"discount":"\u20ac0.00",
	"taxes":[],
	"total":"\u20ac0.00",
	"tags":"",
	"payment_details":"",
	"notes":"",
	"state":"draft",
	"url":"http://endeve.com/my-account/api/v1/estimates/50603e722f412e0435000024.json"
  },
  {  
	"id":"50603e722f412e0435000144",
	"number":"0000005",
	"issue_date":"2012-09-24",
	"contact":{
	  "id":"5059bdbf2f412e0901000044",
	  "full_name":"Cookie Monster"
	},
	"po_number":"",
	"currency":"EUR",
	"items":[
	  {
        "description":"Cookies",
		"quantity":"1.0",
		"unit_price":"0.0",
		"discount_rate":"0.0",
		"tax_1_name":"",
		"tax_1_rate":"",
		"tax_2_name":"",
		"tax_2_rate":"",
		"subtotal":"\u20ac0.00",
		"discount":"\u20ac0.00",
		"gross_amount":"\u20ac0.00"
	   }
    ],
	"subtotal":"\u20ac0.00",
	"discount":"\u20ac0.00",
	"taxes":[],
	"total":"\u20ac0.00",
	"tags":"",
	"payment_details":"",
	"notes":"",
	"state":"draft",
	"url":"http://endeve.com/my-account/api/v1/estimates/50603e722f412e0435000144.json"
  },
]
```

## Get estimate
`GET /estimates/1.json` will return the specified estimate.
```json
{  
  "id":"50603e722f412e0435000024",
  "number":"0000003",
  "issue_date":"2012-09-24",
  "contact":{
    "id":"5059bdbf2f412e0901000024",
    "full_name":"Wild E. Coyote"
  },
  "po_number":"",
  "currency":"EUR",
  "items":[
  	{
	  "description":"ACME TNT",
	  "quantity":"1.0",
	  "unit_price":"100.0",
	  "discount_rate":"0.0",
  	  "tax_1_name":"",
	  "tax_1_rate":"",
	  "tax_2_name":"",
	  "tax_2_rate":"",
	  "subtotal":"\u20ac0.00",
	  "discount":"\u20ac0.00",
	  "gross_amount":"\u20ac0.00"
	}
  ],
  "subtotal":"\u20ac0.00",
  "discount":"\u20ac0.00",
  "taxes":[],
  "total":"\u20ac0.00",
  "tags":"",
  "payment_details":"",
  "notes":"",
  "state":"draft",
  "url":"http://endeve.com/my-account/api/v1/estimates/50603e722f412e0435000024.json"
}
```
## Deliver estimate
`GET /estimates/1/deliver.json` will send the estimate to the contact email.

## Create estimate
`POST /estimates.json` will create a new estimate from the parameters passed.
```json
{
  "number":"0000006",
  "contact_id":"50603e722f412e0435000024",
  "contact_name":"Wild E. Coyote",
  "po_number":"",
  "currency":"EUR",
  "items":[
    {
	  "description":"ACME Catapult",
	  "quantity":"1.0",
	  "unit_price":"0.0",
	  "discount_rate":"0.0",
	  "tax_1_name":"",
	  "tax_1_rate":"",
	  "tax_2_name":"",
	  "tax_2_rate":""
	}
  ],
  "tags":"tnt",
  "payment_details":"",
  "notes":""
}
```

This will return `201 Created`, with the location of the new estimate in the Location header along with the current JSON representation of the estimate if the creation was a success.  If the user does not have access to create new estimates, you'll see `403 Forbidden`.


## Update estimate
`PUT /estimates/1.json` will update the estimate from the parameters passed.
```json
{
  "contact_id":"505c3b402f412e0248000044",
  "contact_name":"Dick Dastardly",
 }
```

This will return `200 OK` if the update was a success along with the current JSON representation of the estimate. If the user does not have access to update the contact, you'll see `403 Forbidden`.


## Delete contact
`DELETE /estimates/1.json` will delete the estimate specified and return `204 No Content` if that was successful. If the user does not have access to delete the estimate, you'll see `403 Forbidden`.