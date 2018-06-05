This is the documentation for EKYC API. This is for all your KYC validation and authentication requirements. 
We help you upload and validate the KYC documents for your customers, vendors, sellers, agents or anyone for that matter. 

## Test API url: https://testtempekyc.mypoolin.com/restful/document_verify

***

## Passing the parameters

The variables below have to be passed using POST action to the url given above with the following field names.


* document_number (Document ID of the user in case of PAN/GST)
* document_type (Document Type (options mentioned below))
* document_file (Raw file) - optional
* document_json - optional


**Please note again that these parameters have to be sent in a POST request.**
If you need to read more about POST requests, please refer to - https://www.w3schools.com/tags/ref_httpmethods.asp

Currently Supported Document Type Values:
1) GST
2) PAN
3) AADHAAR

Future Document Type Values that we will support: 
* COI (Certificate of Incorporation)
* LLP (Partnership LLP Agreement) 
* SOCIETY (Society Resolution Certificate) 
* TRUST (Trust Resolution Certificate) 



``` Sample Request -
curl -iX POST https://testtempekyc.mypoolin.com/restful/document_verify -d "document_number=AUPPV6931E" -d "document_type=PAN" -H "apikey: API_KEY" 


Status Code 
1) 401: The API_KEY passed is not for the ekyc merchant or is not a valid key
   Sample Response -
  {"document_details":null,"is_document_valid":null,"message":"merchant_type is not kyc","status":"error","url":null}

2) 200: Successful Processing of request.
   Sample Response -
   {"document_details":{"dob":"1992-09-26","name":"Dummy Name","pan":"AUEPV5921E","verified":true},"is_document_valid":true,"message":"success","status":"ok"} ```
