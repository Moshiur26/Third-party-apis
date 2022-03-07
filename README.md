# Third-party-apis
BASE_URL = "http://api.shopoth.net/3ps/"
Authentication

* **URL**: `{BASE_URL}/api/v1/login/`

* **Method:** `POST`

*  **Headers:**
	 ``
*  **Params:**

params do
 requires :username, type: String
 requires :password, type: String
end

* **Success Response:**
* **Code:** `200`
  	* **Content:**

```json
{
   "success": true,
   "status_code": 200,
   "message": "Successfully logged in.",
   "data": {
       "token": "eyJhbGciOiJIUzI1NiJ9.IiQyYSQxMiRZZFdkOTdUZ0ZXUFBLUUNuUGpvbG9PZnV3dnBhamhZMXQ3VnF4TFNjUUlEZ0ZtM2ZoSEhOZSI.zUWGkcZm-55SrECarrNHH64EApY7Iz3MHyCmHM04X5M",
       "name": "Jon",
       "phone": "01759408190",
        "username": "jon@agami.ltd"
   }
}
 

```


* ** Error Response:**
* **Code:** `403`
  	* **If username or password not matched then:**
  	* **Content:**
```json
{
   "success": false,
   "status_code": 403,
   "message": "Invalid username or password",
   "data": []
}

```


RA Create

* **URL**: `{BASE_URL}/api/v1/retailer_assistants`

* **Method:** `POST`

*  **Headers:**
	 `Authorization: token’`

*  **Params:**
 requires :name, type: String
 requires :phone, type: String
 optional :email, type: String
 requires :password, type: String
 requires :password_confirmation, type: String
 requires :category, type: String, default: 'dedicated', values: ['dedicated', 'product_push']
 optional :father_name, type: String
 optional :experience, type: String
 optional :education, type: String
 optional :date_of_birth, type: DateTime
 optional :nid, type: String
 optional :tech_skill, type: String
 requires :warehouse_id, type: Interger

* **Success Response:**
* **Code:** `201`
  	* **Content:**

```json
 {
   "success": true,
   "message": "successfully created",
   "status_code": 201
}
```

* ** Error Response:*
* **Code:** '409'
  	* **If any error occurred then:**
  	* **Content:**
```json
{  "success" : false
   "message": "Can not create due to Validation failed: Email has already been taken",
   "status_code": 409
}
```

* ** Error Response:*
* **Code:** '400'
  	* **If any error occurred which is missing any required fields then:**
  	* **Content:**
```json
{  "success" : false
   "message": "name missing",
   "status_code": 400
}
```

Customer List Of a Specific Retailer Assistance(RA)

* **URL**: `{BASE_URL}/api/v1/retailer_assistants/customers`

* **Method:** `GET`

*  **Headers:**
	 `Authorization: token’`

*  **Params:**
 optional :ra_phone, type: String
 requires :start_date_time, type: DateTime
 requires :end_date_time, type: DateTime


* **Success Response:**
* **Code:** '200'
  	* **Content:**

```json
 {
   "success": true,
   "message": "successfully fetch",
   "data": [
   {
      
       "name": "Rakibal Hasan",
       "phone": "01745895099",
       "email": "rakibalhasan448@gmail.com",
       "ra_phone": "01914840253",
       "status": "active",
    
   },
   {
 
       "name": "Atik Hasan Rikcon",
       "phone": "01907645765",
       "email": "atikhsarker@gmail.com",
       "ra_phone": "01914840257",
       "status": "active"
   }
]
,
   "status_code": 200
}
```

* ** Error Response:*
* **Code:** `404`
  	* **If retailer assistance not present:**
  	* **Content:**
```json
{
   "success": true,
   "message":"Retailer Assistance Not Found",
   "status_code": 404,
   "data": [],
}
```

* ** Error Response:*
* **Code:** `500`
  	* **If any error occurs:**
  	* **Content:**
```json
{
   "success": false,
   "message": "Internal server error",
   "status_code": 500,
   "data": {},
}
```

MISFIT will consume
Get partner list of a RA : 
Partner Id,
Name,
Bangla Name,
Status,
Schedule,
Retailer code,
Partner code,


User information what we can able to provide:
Full name,
Phone,
Gender,
Email,
Age,
 

