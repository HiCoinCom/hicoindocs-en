2.13 Batch Get Deposit Records
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:URI: /api/billing/depositList
:Method: GET
:Request Parameters:

=========== =========== =========== =========================================================
Params	    Type	      Required	  Description
ids	        string	    Y	          multiple 'id' are separated by commas, up to 100 id
app_id	    string	    Y	          app id
time	      long	      Y	          timestamp
sign	      string	    Y	          sign value
=========== =========== =========== =========================================================


:Request Parameters:

=========== =========== =========== ============================================
Params	    Type	      Required	  Description
code	      string	    Y	          error code，0 means success
msg         string      Y           error code description
data	      json	      Y	          response data
=========== =========== =========== ============================================

:Data Structure:

============== =========== =========== ==================================================================================
Params         Type        Required    Description
id             int         Y           deposit record id
uid            int         Y           user id
symbol         String      Y           symbol name
amount         String      Y           deposit amount
created_at     String      Y           create time
updated_at     String      Y           update time
txid           String      Y           transaction id in blockchain
confirmations  int         Y           confirmations in blockchain
address_to     String      Y           deposit address
status         int         Y           deposit status, 0:waiting for confirmation，1: complete 2: failure
============== =========== =========== ==================================================================================


:Response Samples:

::

	{
		"code": "0",
		"msg": "suc",
		"data": [
			{
				"id" ：1,
				"uid" ：11,
				"symbol"："ETH",
				"amount"："0.0002000000000000",
				"created_at": 1545273830000,
				"updated_at": 1545273830000,
				"txid":"78d1edef3b3fd14365f88cf2d03e8c29ec49ac1a43cedde9e21d320b3268f4de",
				"confirmations":11,
				"status":1,
				"address_to":"0xcb03bfdccb50c9f62ec1c728f264bf453e037132"
			},
			{
				"id" ：2,
				"uid" ：12,
				"symbol" ："ETH",
				"amount"："0.0002000000000000",
				"created_at": 1545273830000,
				"updated_at": 1545273830000,
				"txid":"0xd609e050c3d573fb715431edbd36cc08eaa475f813de921026a65c0a96e8113e",
				"confirmations":11,
				"status":1,
				"address_to":"0xcb03bfdccb50c9f62ec1c728f264bf453e037132"
			}
		]
	}
