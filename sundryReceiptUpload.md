**SundryReceiptUpload**
----
	Returns "success" and a count of updated receipt(s), or a structure of invalid validations "__invalid" belonging to receipt(s).

* **Version History:**

    TASS v53.0 - Method Added.

* **Version:**

	2
    
* **Method:**

	`GET | POST`
	
*  **Params:**

	**Required:**
 
	`submit_time [date]` - submit_time.

	`trans_amt [decimal]` - trans_amt.

	`batch_num [number]` - batch_num.

	`sundry_name [string]` - sundry_name.

	`comment [string]` - comment.

	`acct_code [string]` - acct_code.

	`dist_amt [decimal]` - dist_amt.

	`tax_amt [decimal]` - tax_amt.

	`tax_code [string]` - tax_code.

	**Optional:**

	`merchant_id [string]` - merchant_id.

	`receipt_num [string]` - receipt_num.

	`addr1 [string]` - addr1.

	`addr2 [string]` - addr2.

	`addr3 [string]` - addr3.

	`town_sub [string]` - town_sub.

	`state_code [string]` - state_code.

	`post_code [string]` - post_code.

	`country [string]` - country.

	**Conditional:**

	`donor_num [number]` - donor_num. Required when [Fundrasing Setup > Enable Donations from Receipting] is set to "automatic", and acct_code supplied is the same as Parents [Accounts Setup > Building Fund Account].OR Required when appeal_code or ple_num supplied.

	`appeal_code [string]` - appeal_code. Required when donor_num is supplied and ple_num is not supplied. If supplied length must be between 1 and 4 Characters.

	`ple_num [number]` - ple_num. Required when donor_num is supplied and appeal_code is not supplied.

* **Success Response:**

	```javascript
	{
	    "success":"You successfully uploaded 1 sundry receipt(s).",
	    "token":{
	        "sundryreceipts":[
	            {
	                "receipt_num":"",
	                "donor_num":"",
	                "seq_num":1,
	                "sundry_name":"Billy Joe",
	                "appeal_code":"",
	                "dist_amt":10,
	                "ple_num":"",
	                "comment":"Sundry Fee",
	                "tax_amt":1,
	                "town_sub":"",
	                "state_code":"",
	                "trans_amt":11,
	                "addr3":"",
	                "addr2":"",
	                "submit_time":"2020-05-26 10:00:00.000",
	                "addr1":"",
	                "country":"",
	                "batch_num":20200129,
	                "acct_code":"01-0290-00-00",
	                "post_code":"",
	                "id":1,
	                "tax_code":"AO",
	                "merchant_id":""
	            }
	        ],
	        "timestamp":"{ts '2020-06-05 09:01:54'}"
	    }
	}
	```
 
* **Error Response:**

	`sundryreceipts` not supplied
	```javascript
	__invalid: {
		"sundryreceipts": "'sundryreceipts' is required."
	}
	```

	`[field_name]` is not valid
	```javascript
	__invalid: {
		"[field_name]": "'[field_name]' is not a valid field name"
	}
	```

	`id` not supplied
	```javascript
	__invalid: {
		"id": "Id is required for all rows."
	}
	```

	`submit_time` not supplied
	```javascript
	__invalid: {
		"submit_time": "'submit_time' is required."
	}
	```

	`trans_amt` not supplied
	```javascript
	__invalid: {
		"trans_amt": "Invalid amount."
	}
	```

	`batch_num` not supplied
	```javascript
	__invalid: {
		"batch_num": "'batch_num' is required."
	}
	```

	`sundry_name` not supplied
	```javascript
	__invalid: {
		"sundry_name": "'sundry_name' is required."
	}
	```

	`comment` not supplied
	```javascript
	__invalid: {
		"comment": "'comment' is required."
	}
	```

	`acct_code` not supplied
	```javascript
	__invalid: {
		"acct_code": "'acct_code' is required."
	}
	```

	`dist_amt` not supplied
	```javascript
	__invalid: {
		"dist_amt": "Invalid amount."
	}
	```

	`tax_amt` not supplied
	```javascript
	__invalid: {
		"tax_amt": "Invalid amount."
	}
	```

	`tax_code` not supplied
	```javascript
	__invalid: {
		"tax_code": "'tax_code' is required."
	}
	```

	`id` has a duplicate value
	```javascript
	__invalid: {
		"id": "Id must be unique for all rows."
	}
	```

	`id` must be same as the sequence number
	```javascript
	__invalid: {
		"seq_num": {
			"n": "ID must be same as the sequence number (seq_num)."
		}
	}
	```

	`id` not integer
	```javascript
	__invalid: {
		"id": "value must be a valid integer."
	}
	```

	`batch_num` not integer
	```javascript
	__invalid: {
		"batch_num": "value must be a valid integer."
	}
	```

	`sundry_name` exceeds 30 characters
	```javascript
	__invalid: {
		"sundry_name": "exceeds 30 characters."
	}
	```

	`comment` exceeds 30 characters
	```javascript
	__invalid: {
		"comment": "exceeds 30 characters."
	}
	```

	`acct_code` exceeds 18 characters
	```javascript
	__invalid: {
		"acct_code": "exceeds 18 characters."
	}
	```

	`tax_code` exceeds 3 characters
	```javascript
	__invalid: {
		"tax_code": "exceeds 3 characters."
	}
	```

	`merchant_id` exceeds 18 characters
	```javascript
	__invalid: {
		"merchant_id": "exceeds 18 characters."
	}
	```

	`receipt_num` exceeds 12 characters
	```javascript
	__invalid: {
		"receipt_num": "exceeds 12 characters."
	}
	```

	`addr1` exceeds 30 characters
	```javascript
	__invalid: {
		"addr1": "exceeds 30 characters."
	}
	```

	`addr2` exceeds 30 characters
	```javascript
	__invalid: {
		"addr2": "exceeds 30 characters."
	}
	```

	`addr3` exceeds 30 characters
	```javascript
	__invalid: {
		"addr3": "exceeds 30 characters."
	}
	```

	`town_sub` exceeds 30 characters
	```javascript
	__invalid: {
		"town_sub": "exceeds 30 characters."
	}
	```

	`state_code` exceeds 3 characters
	```javascript
	__invalid: {
		"state_code": "exceeds 3 characters."
	}
	```

	`post_code` exceeds 10 characters
	```javascript
	__invalid: {
		"post_code": "exceeds 10 characters."
	}
	```

	`country` exceeds 20 characters
	```javascript
	__invalid: {
		"country": "exceeds 20 characters."
	}
	```

	`trans_amt` not valid amount
	```javascript
	__invalid: {
		"trans_amt": "Invalid amount."
	}
	```

	`dist_amt` not valid amount
	```javascript
	__invalid: {
		"dist_amt": "Invalid amount."
	}
	```

	`tax_amt` not valid amount
	```javascript
	__invalid: {
		"tax_amt": "Invalid amount."
	}
	```

	`trans_amt` more than 2 decimal places
	```javascript
	__invalid: {
		"trans_amt": "The Transaction Amount [trans_amt] field has more than 2 decimal places."
	}
	```

	`dist_amt` more than 2 decimal places
	```javascript
	__invalid: {
		"dist_amt": "The Dist Amount [dist_amt] field has more than 2 decimal places."
	}
	```

	`tax_amt` more than 2 decimal places
	```javascript
	__invalid: {
		"tax_amt": "The Tax Amount [tax_amt] field has more than 2 decimal places."
	}
	```

	`trans_amt` not equal to `dist_amt` plus `tax_amt`
	```javascript
	__invalid: {
		"seq_num": "Payment Amount does not equal Nett Distribution Amount + Tax Amount."
	}
	```

	`submit_time` accounting period is closed or not setup. 
	```javascript
	__invalid: {
		"id": "Accounting Period closed or not setup for [submit_time]."
	}
	```

	`acct_code` is invalid or closed. 
	```javascript
	__invalid: {
		"id": "GL Account #args.acct_code# is invalid or is closed."
	}
	```

	Checking duplicated record.
	```javascript
	__invalid: {
		"id": "Duplicate Entry - An entry with this Sundry Name, Date and Line Number already exists."
	}
	```

	`tax_amt` not valid amount
	```javascript
	__invalid: {
		"tax_amt": "Invalid amount."
	}
	```

	`donor_num [number]` - donor_num. Required when [Fundrasing Setup > Enable Donations from Receipting] is set to "automatic", and acct_code supplied is the same as Parents [Accounts Setup > Building Fund Account].OR Required when appeal_code or ple_num supplied.

	`appeal_code [string]` - appeal_code. Required when donor_num is supplied and ple_num is not supplied. If supplied length must be between 1 and 4 Characters.

	`ple_num [number]` - ple_num. Required when donor_num is supplied and appeal_code is not supplied.

	`donor_num` not supplied when required when [Fundrasing Setup > Enable Donations from Receipting] is set to "automatic", and acct_code supplied is the same as Parents [Accounts Setup > Building Fund Account]
	```javascript
	__invalid: {
		"id": "Donor Number must be specified."
	}
	```

	`donor_num` not supplied when appeal_code is supplied
	```javascript
	__invalid: {
		"id": "Donor Number must be specified where a Appeal Code is specified."
	}
	```

	`donor_num` not supplied when ple_num is supplied
	```javascript
	__invalid: {
		"id": "Donor Number must be specified where a Pledge Number is specified."
	}
	```

	`donor_num` invalid or not a number
	```javascript
	__invalid: {
		"id": "Donor Number [donor_num] is invalid."
	}
	```

	`ple_num` is invalid or not a number
	```javascript
	__invalid: {
		"id": "Pledge Number is invalid."
	}
	```

	`appeal_code` and `ple_num` not supplied when donor_num is supplied
	```javascript
	__invalid: {
		"id": "Pledge Number is invalid."
	}
	```

	`appeal_code` invalid
	```javascript
	__invalid: {
		"id": "Appeal Code [appeal_code] is invalid."
	}
	```

	`appeal_code` supplied when ple_num also supplied
	```javascript
	__invalid: {
		"id": "Appeal Code must be null where a Pledge Number is specified."
	}
	```

	`ple_num` does not match donor_num
	```javascript
	__invalid: {
		"id": "Pledge Number [ple_num] is not a valid pledge for Donor Number [donor_num]."
	}
	```

* **Sample Parameters:**

	```javascript
	{
		"sundryreceipts":
		[
			{
				"id":"1",
				"submit_time":"2020-05-26 10:00:00.000",
				"trans_amt":"11.00",
				"batch_num":"20200129",
				"sundry_name":"Billy Joe",
				"comment":"Sundry Fee",
				"acct_code":"01-0290-00-00",
				"dist_amt":"10.00",
				"tax_amt":"1.00",
				"tax_code":"AO"
			}
		]
	}
	```

* **Sample GET:** (With URL Encoded `token`)

	```HTML
	http://api.tasscloud.com.au/tassweb/api/?method=sundryReceiptUpload&appcode=API21&company=10&v=2&token=BJVvYXC0We4Dtvp6Q49RqhBeAi6uqpTQ9t%2FKI9ZAFpCMeVXIFlDU5yNQIeYME%2BYLXgYA69RTUjXjLeVBetN6CaFMdPCKMWBXD%2Bkkt0%2Fuht0suYrSDONP6mx%2Fbt4WGgNOD5YoIYRNiIVDw2Qn2Oi5YodaEUgtGJohUJMzy3tqsX%2BraZk3j7d77okDCjb7MeFJ0DcupqUoRiGjE39415HTfPgNc6R6BY9wt7SJsj4yOPBrIxHQVS8Yy6gZ3nZgsJ5rhcdkB6eCI6b3FJ31s6vsVcbVu5NBY8AF1qqjWLMazduISzEBwRDsofXfJjo1KLX59R410bmbrF5Z7QZfEfE%2FlettTWOyb4EgdhBoC3v0aLOfF6Bt12AFXDo2VGbgryceeOLAscp%2FFr9ttH42hClBtWsxFU1N5dDENUsVHOwWcfCxd7aTtc0xjvaEYJWcZrRRZa1yrIvgeWaDk0LVxM5ePcT%2BltdrymgmxmZYgxdiYC1qQDcNXDx9hN7yKeZDUztwGA0yl2iXW8aBXAy5hRnztR0TrREyOba26mUHxUJO7tfpIyOrpPbE0nR18vtCZ%2BinbvyqN9adpZhQPByG2XD9M6MoYdmBCc3Duv9qb%2BIa0A8%3D
	```
	
* **Sample POST:**

	```HTML
	<form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
		 <input type="hidden" name="method" value="sundryReceiptUpload">
		 <input type="hidden" name="appcode" value="API21">
		 <input type="hidden" name="company" value="10">
		 <input type="hidden" name="v" value="2">
		 <textarea name="token">BJVvYXC0We4Dtvp6Q49RqhBeAi6uqpTQ9t/KI9ZAFpCMeVXIFlDU5yNQIeYME+YLXgYA69RTUjXjLeVBetN6CaFMdPCKMWBXD+kkt0/uht0suYrSDONP6mx/bt4WGgNOD5YoIYRNiIVDw2Qn2Oi5YodaEUgtGJohUJMzy3tqsX+raZk3j7d77okDCjb7MeFJ0DcupqUoRiGjE39415HTfPgNc6R6BY9wt7SJsj4yOPBrIxHQVS8Yy6gZ3nZgsJ5rhcdkB6eCI6b3FJ31s6vsVcbVu5NBY8AF1qqjWLMazduISzEBwRDsofXfJjo1KLX59R410bmbrF5Z7QZfEfE/lettTWOyb4EgdhBoC3v0aLOfF6Bt12AFXDo2VGbgryceeOLAscp/Fr9ttH42hClBtWsxFU1N5dDENUsVHOwWcfCxd7aTtc0xjvaEYJWcZrRRZa1yrIvgeWaDk0LVxM5ePcT+ltdrymgmxmZYgxdiYC1qQDcNXDx9hN7yKeZDUztwGA0yl2iXW8aBXAy5hRnztR0TrREyOba26mUHxUJO7tfpIyOrpPbE0nR18vtCZ+inbvyqN9adpZhQPByG2XD9M6MoYdmBCc3Duv9qb+Ia0A8=</textarea>
	</form>
	```
