# Billable-Hours-GA
This application creates a billable rate for Lawyers and makes revenue collection easier. Its usage is seamless and accurate.

1. POST - Parse CSV file content
* Endpoints: {{baseUrl}}/invoice/parse
* Description: This endpoint allows you to parse the content of the CSV file encoded in Base64.
  The CSV file must tally with the specified format.


* Request:
  HEADERS: Content-Type
  (application/json)

  Body

  {
    "payload": "Base64-encoded CSV content"
  }


*Response
"This endpoint will return a response with the parsed data in JSON format.

2. GET - Get Invoice Parsing Result by Id.
   * Endpoint:
   {{baseUrl}}/invoice/{{invoice_id}}

   * Description: Retrieve the parsed CSV invoice by its specified ID.
  
   * Request:
       curl --location -g '{{baseUrl}}/invoice/:invoiceId'
   * Response:
       * Returns JSON data with parsed company details and an empty map when the specified Id is not found.

         {
      "companies": { "Google": 2400, "Facebook": 500
      }, "id": "<uuid>"
         }
  
3. GET - Get Company Details from an Invoice
   *Endpoint:
   {{baseUrl}}/invoice/{{invoice_id}}/company?companyName=Google
   *Description: Get a breakdown of the employees, rates, and amounts billed by a company in an invoice result using the Id.

   * Request:
     curl --location -g '{{baseUrl}}/invoice/:invoiceId/company?companyName=Facebook'

   * Response:
       * Returns JSON data with detailed company billing information.

