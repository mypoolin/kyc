This is the documentation for EKYC API. This is for all your KYC validation and authentication requirements. 
We help you upload and validate the KYC documents for your customers, vendors, sellers, agents or anyone for that matter. 

## Test API url: https://tempkyc.mypoolin.com/restful/document_verify

***

## Passing the parameters

The variables below have to be passed using POST action to the url given above with the following field names.

* merchant_name (your merchant username/key Example: test-name-p2m. You would have received this in your signup email with us under the subject line 'Welcome to WibmoPay!')
* document_number (Document ID of the user in case of PAN/GST)
* document_type (Document Type (options mentioned below))
* checksum (creation process is described below) 
* document_file (Name of the user) - optional
* document_json - optional


**Please note again that these parameters have to be sent in a POST request.**
If you need to read more about POST requests, please refer to - https://www.w3schools.com/tags/ref_httpmethods.asp

Currently Supported Document Type Values:
1) GST
2) PAN
3) AADHAAR

Future Document Type Values that we will support: 
4) COI (Certificate of Incorporation)
5) LLP (Partnership LLP Agreement) 
6) SOCIETY (Society Resolution Certificate) 
7) TRUST (Trust Resolution Certificate) 

## Checksum creation and usage

Checksum is a field used to validate the parameters of the transaction and ensure the request made by you is genuine. This is mandatory and the creation process is described below. 

To create the checksum you will require the following fields:

1. Username (your merchant username)
2. Document Number (Document ID)
3. Secret/API Key (your merchant secret)

(You would have received this in your signup email with us under the subject line 'Welcome to WibmoPay!')

You need create a verifying string in the following manner:

```
username|document_number|secret
```

Here you are using | (pipe) as a separator. Now you will hash this verifying string with sha512 algorithm
and pass it in the calls. 

Status Code 
1) Success 
2) Fail

## Pseudocode For CheckSum Generation

You can find below the steps to be followed for generating the checksum when making the POST request. 
Also, pseudo code is written below to give you an idea. 

1. Initialize an array and put in elements as 
     arr = [username, document_number, secret]

2. Concatenate elements in array with pipe(|)  
     for (data in arr){  
     checksum_str  += str(data) + '|'  
     }
    
     checksum_str = checksum_str[:-1]  

3. Generate hash512  
     return hashlib.sha512(checksum_str).hexdigest().upper()

For further queries please reach out to the developers on backend@mypoolin.com

## Sample Code for checksum in Python  
```py
import hashlib  
arr = [username, document_number, secret] 
checksum_str = ''  
for data in arr:  
   checksum_str  += str(data) + '|'  

checksum_str = checksum_str[:-1]  
return hashlib.sha512(checksum_str).hexdigest().upper()  
```
## Sample Code for checksum in PHP  
```php
<?php  
$arr = array(username, document_number, secret);  
$checksum_str = '';  
foreach ($arr as $data){  
  $checksum_str  .= (string)$data . '|';  
}  

$checksum_str = substr($checksum_str, 0, -1);  
return strtoupper(hash("sha512", $checksum_str));  
?>  
```

## Sample Code for Checksum in Node JS  
```js
var crypto = require('crypto');  
var arr = [username, document_number, secret];  
var checksum_str = '';  
for(var i = 0;i<arr.length;i++){  
	checksum_str +=  arr[i] + '|';  
}  

checksum_str = checksum_str.substring(0, checksum_str.length - 1);  
return crypto.createHash('sha512').update(String(checksum_str)).digest('hex').toUpperCase();  
```
