This is the documentation for EKYC API. This is for all your KYC validation and authentication requirements. 
We help you upload and validate the KYC documents for your customers, vendors, sellers, agents or anyone for that matter. 

## Test API url: https://testtempekyc.mypoolin.com/kyc_verification

***

## Passing the parameters

The variables below have to be passed using POST action to the url given above with the following field names.

* checksum (creation process is described below) 
* merchant_name (your merchant username/key eg-test-name-ekyc)
* merchant_txn_id (your transaction id eg - 12345ABCDE)
* entity_name (Name of the user) 
* doc_types (comma separated payment mode you want eg -gstin,individual_pan,company_pan) - optional



**Please note again that these parameters have to be sent in a POST request.**
If you need to read more about POST requests, please refer to - https://www.w3schools.com/tags/ref_httpmethods.asp

Currently Supported Document Type Values:
1) GST - gstin
2) PAN - individual_pan
3) PAN - company_pan

Future Document Type Values that we will support: 
* COI (Certificate of Incorporation)
* LLP (Partnership LLP Agreement) 
* SOCIETY (Society Resolution Certificate) 
* TRUST (Trust Resolution Certificate) 


## Checksum creation and usage

Checksum is a field used to validate the parameters of the transaction.
To create the checksum we will require the following fields:

1. Merchant Transaction ID (merchant_txn_id)
2. Documents to be validated (doc_types)
3. Username (your merchant username)
4. Secret/API Key (your merchant secret)

We create a verifying string in the following manner:

```
merchant_txn_id|doc_types|username|secret
```

Here we are using | (pipe) as a separator. Now we will hash this verifying string with sha512 algorithm
and pass it in the calls

The status of document can be of the following types:
1. VERIFIED
2. INVALID

