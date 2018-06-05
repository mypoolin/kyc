This is the documentation for EKYC API. This is for all your KYC validation and authentication requirements. 
We help you upload and validate the KYC documents for your customers, vendors, sellers, agents or anyone for that matter. 

## Test API url: https://tempkyc.mypoolin.com/restful/document_verify

***

## Passing the parameters

The variables below have to be passed using POST action to the url given above with the following field names.

* merchant_name (your merchant username/key Example: test-name-p2m. You would have received this in your signup email with us under the subject line 'Welcome to WibmoPay!')
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
4) COI (Certificate of Incorporation)
5) LLP (Partnership LLP Agreement) 
6) SOCIETY (Society Resolution Certificate) 
7) TRUST (Trust Resolution Certificate) 


A sample POST form would like this below - 
<form action="https://tempkyc.mypoolin.com/restful/document_verify" method="POST">
  	<input type="hidden" name="document_type" value="PAN">
  	<input type="hidden" name="merchant_name" value="test-shobhit-kyc">
  	<input type="hidden" name="document_number" value="12345ABCDE">
 </form>

Status Code 
1) Success 
2) Fail

