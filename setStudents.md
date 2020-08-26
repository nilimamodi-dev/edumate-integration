**setStudents**
----
	Returns "success" and a count of updated and/or failed students, or a structure of invalid validations "__invalid" belonging to student(s).
  
* **Version History:**

    TASS v53.2.nnn - Method Added.

* **Version:**

	2

* **Method:**

	`GET | POST`
	
*  **Params:**

	**Required:**
 
	`data [array]` - Array of Students to be updated

	`id [string]` - Student Code sourced from Edumate

	`surname [string]` - Surname. Length must be between 1 and 30 Characters

	`date_of_entry [date dd/mm/yyyy or yyyy-mm-dd]` - Date of Entry

	`boarder [string]` - Boarder flag. Length must be 1 Character (Y/N)
	
	`parent_code [string]` - Parent Code sourced from Edumate
	
	`first_name [string]` - First Name. Length must be between 1 and 50 Characters
	
	`gender [string]` - Gender. Length must be between 1 and 3 Characters and a valid Gender in TASS
	
	`year_group [string]` - Year Group. Length must be between 1 and 2 Characters
	
	`multiparent_flg [string]` - Multi Parent Flag. Length must be 1 Character (Y/N)
	
	`distance_ed [string]` - Distance Education flag. Length must be 1 Character (Y/N)

	**Optional:**

	`other_name [string]` - Other Name.

	`preferred_surname [string]` - Preferred Surname (use surname if not supplied).

	`preferred_name [string]` - Preferred name (use first name if not supplied).
	
	`alternate_id [string]` - Alt ID (Must be a unique value against any student in the database and the submitted list)

	`form_class [alphanumeric]` - Form Class (No spaces or special chars)

	`fte [decimal (1,2)]` - FTE (Range 0.00 to 1.00 only)

	`house [string]` - House (Must be an existing House)

	`religion [string]` - Religion (Must be an existing Religion)

	`pc_tutor_group [alphanumeric]` - PC Tut Group (No spaces or special chars)

	`campus [string]` - Campus (Must be an existing Campus)

	`e_mail [string]` - E Mail

	`resident_status [string]` - Resident Status (Must be an existing Resident Status)

	`visa_expiry [date dd/mm/yyyy or yyyy-mm-dd]` - Visa Expiry

	`visa_subclass [string]` - Visa Subclass

	`date_of_arrival [date dd/mm/yyyy or yyyy-mm-dd]` - Date of Arrival

	`ffpos [string]` - FFPOS (Y or N). If supplied, length must be 1.

	**Conditional:**

	`mob_phone [string]` - Mobile Phone. Required if sms_flg is present.

	`sms_flg [string]` - SMS Flag (Y or N) Required if mob_phone is present. If supplied, length must be 1.




* **Success Response:**

	```javascript
	{
		"success": "You successfully saved 1 student(s).",
		"__tassversion": "01.052.0.999",
		"token": {
			"data": [
				{
					"date_of_leaving": "",
					"distance_ed": "N",
					"resident_status": "Australian Citizen",
					"year_group": -1,
					"first_name": "Logan",
					"ffpos": "N",
					"campus": "International",
					"preferred_name": "",
					"boarder": "N",
					"gender": "M",
					"id": 1876543218,
					"house": "Acacia",
					"date_of_birth": "2005-05-02",
					"alternate_id": "008665443z",
					"surname": "Edumate",
					"pc_tutor_group": "A1",
					"date_of_arrival": "2018-08-24",
					"preferred_surname": "",
					"e_mail": "test@tassweb.com.au",
					"mobile_phone": "0425889552",
					"parent_code": "2147483641",
					"sms_flg": "Y",
					"multiparent_flg": "N",
					"visa_subclass": "Sup",
					"religion": "Baptist",
					"fte": 1,
					"other_name": "Jimmy",
					"date_of_entry": "2020-08-01",
					"visa_expiry": "2028-01-01"
				}
			],
			"timestamp": "{ts '2020-08-26 16:21:48'}"
		}
	}
	```
 
* **Error Response:**

	Date `[field_name]` not a valid date
	```javascript
	__invalid: {
		"[field_name]": "Value is not a valid date."
	}
	```
	
	Decimal `[field_name]` not a valid decimal
	```javascript
	__invalid: {
		"[field_name]": "Value is not a valid decimal."
	}
	```


	`data` not supplied
	```javascript
	__invalid: {
		"data": "'data' is required"
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

	`id` has a duplicate value
	```javascript
	__invalid: {
		"id": "'fieldvalue' is a duplicate `id`"
	}
	```

	`surname` length less than 1
	```javascript
	__invalid: {
		"surname": "surname is required"
	}
	```

	`preferred_name` length less than 1
	```javascript
	__invalid: {
		"preferred_name": "preferred_name is required"
	}
	```

	`surname` exceed 30 characters
	```javascript
	__invalid: {
		"surname": "The value for this field exceeds the length permitted (NN of 30)."
	} 
	```

	`preferred_name` exceed 20 characters
	```javascript
	__invalid: {
		"preferred_name": "The value for this field exceeds the length permitted (NN of 20)."
	} 
	```

	`alternate_id` exceed 40 characters
	```javascript
	__invalid: {
		"alternate_id": "The value for this field exceeds the length permitted (NN of 40)."
	} 
	```

	`alternate_id` is not unique in the database or supplied list of students
	```javascript
	__invalid: {
		"alternate_id": "Value is not unique"
	} 
	```

	`form_class` exceed 1 characters
	```javascript
	__invalid: {
		"form_class": "The value for this field exceeds the length permitted (NN of 1)."
	} 
	```

	`form_class` contains invalid characters (other than A-Z and 0-9)
	```javascript
	__invalid: {
		"form_class": "Value is not a valid alphanumeric code."
	} 
	```

	`parent_code` exceeds 8 characters
	```javascript
	__invalid: {
		"parent_code": "The value for this field exceeds the length permitted (NN of 8)."
	} 
	```

	`parent_code` is not a valid parent
	```javascript
	__invalid: {
		"parent_code": "'[parent_code]' is not a valid Parent"
	} 
	```

	`house` exceed 20 characters
	```javascript
	__invalid: {
		"house": "The value for this field exceeds the length permitted (NN of 20)."
	} 
	```

	`house` does not exist in the database
	```javascript
	__invalid: {
		"house": "house does not exist"
	} 
	```

	`gender` exceed 3 characters
	```javascript
	__invalid: {
		"gender": "The value for this field exceeds the length permitted (NN of 3)."
	} 
	```

	`gender` does not exist in the database
	```javascript
	__invalid: {
		"gender": "'[gender]' is not a valid Gender"
	} 
	```

	`religion` exceed 22 characters
	```javascript
	__invalid: {
		"religion": "The value for this field exceeds the length permitted (NN of 22)."
	} 
	```

	`religion` does not exist in the database
	```javascript
	__invalid: {
		"religion": "'[religion]' is not a valid Religion"
	} 
	```

	`pc_tutor_group` exceed 5 characters
	```javascript
	__invalid: {
		"pc_tutor_group": "The value for this field exceeds the length permitted (NN of 5)."
	} 
	```

	`pc_tutor_group` contains invalid characters (other than A-Z and 0-9)
	```javascript
	__invalid: {
		"pc_tutor_group": "Value is not a valid alphanumeric code."
	} 
	```

	`campus` exceed 50 characters
	```javascript
	__invalid: {
		"campus": "The value for this field exceeds the length permitted (NN of 50)."
	} 
	```

	`campus` does not exist in the database
	```javascript
	__invalid: {
		"campus": "'[campus]' is not a valid Campus"
	} 
	```

	`e_mail` exceed 60 characters
	```javascript
	__invalid: {
		"e_mail": "The value for this field exceeds the length permitted (NN of 60)."
	} 
	```

	`e_mail` not in the correct format
	```javascript
	__invalid: {
		"e_mail": "e_mail is not valid"
	} 
	```

	`mobile_phone` exceed 30 characters
	```javascript
	__invalid: {
		"mobile_phone": "The value for this field exceeds the length permitted (NN of 30)."
	} 
	```

	`mobile_phone` or `sms_flg` is not supplied
	```javascript
	__invalid: {
		"mobile_phone": "mobile_phone and sms_flg must be submitted together"
	} 
	```

	`sms_flg` exceed 1 characters
	```javascript
	__invalid: {
		"sms_flg": "The value for this field exceeds the length permitted (NN of 1)."
	} 
	```

	`sms_flg` must be Y or N
	```javascript
	__invalid: {
		"sms_flg": "sms_flg must be either Y or N"
	} 
	```

	`multiparent_flg` must be Y or N
	```javascript
	__invalid: {
		"multiparent_flg": "multiparent_flg must be either Y or N"
	} 
	```

	`ffpos` must be Y or N
	```javascript
	__invalid: {
		"ffpos": "ffpos must be either Y or N"
	} 
	```

	`resident_status` exceed 50 characters
	```javascript
	__invalid: {
		"resident_status": "The value for this field exceeds the length permitted (NN of 50)."
	} 
	```

	`visa_subclass` exceed 6 characters
	```javascript
	__invalid: {
		"visa_subclass": "The value for this field exceeds the length permitted (NN of 6)."
	} 
	```

	`fte` has more than 2 decimal points
	```javascript
	__invalid: {
		"fte": "Value has more than 2 decimal points."
	}
	```

	
* **Sample Parameters:**

	```javascript
	{
	    "data":
	    [
	        {
	            "id" : "1876543218"
	            , "date_of_entry" : "2020-08-01"
	            , "boarder" : "N"
	            , "parent_code" : "2147483641"
	            , "surname" : "Edumate"
	            , "first_name" : "Logan"
	            , "gender" : "M"
	            , "year_group" : "-1"
	            , "multiparent_flg" : "N"
	            , "distance_ed" : "N"
	            , "fte" : "1.00"
	            , "pc_tutor_group" : "A1"
	            , "date_of_leaving" : ""
	            , "date_of_birth" : "2005-05-02"
	            , "date_of_arrival" : "2018-08-24"
	            , "other_name" : "Jimmy"
	            , "preferred_name" : ""
	            , "preferred_surname" : ""
	            , "alternate_id" : "008665443z"
	            , "e_mail" : "test@tassweb.com.au"
	            , "mobile_phone" : "0425889552"
	            , "sms_flg" : "Y"
	            , "visa_expiry" : "2028-01-01"
	            , "visa_subclass" : "Sup"
	            , "ffpos" : "N"
	            , "house" : "Acacia"
	            , "religion" : "Baptist"
	            , "campus" : "International"
	            , "resident_status" : "Australian Citizen"
	        }
	    ]
	}
	```

* **Sample GET:** (With URL Encoded `token`)

	```HTML
	http://api.tasscloud.com.au/tassweb/api/?method=setStudents&appcode=DEMOAP&company=10&v=2&token=BJVvYXC0We4Dtvp6Q49RqhBeAi6uqpTQ9t%2FKI9ZAFpCMeVXIFlDU5yNQIeYME%2BYLXgYA69RTUjXjLeVBetN6CaFMdPCKMWBXD%2Bkkt0%2Fuht0suYrSDONP6mx%2Fbt4WGgNOD5YoIYRNiIVDw2Qn2Oi5YodaEUgtGJohUJMzy3tqsX%2BraZk3j7d77okDCjb7MeFJ0DcupqUoRiGjE39415HTfPgNc6R6BY9wt7SJsj4yOPBrIxHQVS8Yy6gZ3nZgsJ5rhcdkB6eCI6b3FJ31s6vsVcbVu5NBY8AF1qqjWLMazduISzEBwRDsofXfJjo1KLX59R410bmbrF5Z7QZfEfE%2FlettTWOyb4EgdhBoC3v0aLOfF6Bt12AFXDo2VGbgryceeOLAscp%2FFr9ttH42hClBtWsxFU1N5dDENUsVHOwWcfCxd7aTtc0xjvaEYJWcZrRRZa1yrIvgeWaDk0LVxM5ePcT%2BltdrymgmxmZYgxdiYC1qQDcNXDx9hN7yKeZDUztwGA0yl2iXW8aBXAy5hRnztR0TrREyOba26mUHxUJO7tfpIyOrpPbE0nR18vtCZ%2BinbvyqN9adpZhQPByG2XD9M6MoYdmBCc3Duv9qb%2BIa0A8%3D
	```
	
* **Sample POST:**

	```HTML
	<form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
		 <input type="hidden" name="method" value="setStudents">
		 <input type="hidden" name="appcode" value="DEMOAP">
		 <input type="hidden" name="company" value="10">
		 <input type="hidden" name="v" value="2">
		 <textarea name="token">BJVvYXC0We4Dtvp6Q49RqhBeAi6uqpTQ9t/KI9ZAFpCMeVXIFlDU5yNQIeYME+YLXgYA69RTUjXjLeVBetN6CaFMdPCKMWBXD+kkt0/uht0suYrSDONP6mx/bt4WGgNOD5YoIYRNiIVDw2Qn2Oi5YodaEUgtGJohUJMzy3tqsX+raZk3j7d77okDCjb7MeFJ0DcupqUoRiGjE39415HTfPgNc6R6BY9wt7SJsj4yOPBrIxHQVS8Yy6gZ3nZgsJ5rhcdkB6eCI6b3FJ31s6vsVcbVu5NBY8AF1qqjWLMazduISzEBwRDsofXfJjo1KLX59R410bmbrF5Z7QZfEfE/lettTWOyb4EgdhBoC3v0aLOfF6Bt12AFXDo2VGbgryceeOLAscp/Fr9ttH42hClBtWsxFU1N5dDENUsVHOwWcfCxd7aTtc0xjvaEYJWcZrRRZa1yrIvgeWaDk0LVxM5ePcT+ltdrymgmxmZYgxdiYC1qQDcNXDx9hN7yKeZDUztwGA0yl2iXW8aBXAy5hRnztR0TrREyOba26mUHxUJO7tfpIyOrpPbE0nR18vtCZ+inbvyqN9adpZhQPByG2XD9M6MoYdmBCc3Duv9qb+Ia0A8=</textarea>
	</form>
	```
