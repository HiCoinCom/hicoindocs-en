
2.11 Batch Get Withdrawal Records
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:URL: /api/billing/withdrawList
:Method: GET
:Request Parameters:

=========== =========== =========== ===================================================================================
Params	    Type	      Required	  Description
ids	        string	    Y	          multiple 'request_id' are separated by commas, up to 100 request_id
app_id	    string	    Y	          app id
time	      long	      Y	          timestamp
sign	      string	    Y	          sign value
=========== =========== =========== ===================================================================================

:Request Parameters:

=========== =========== =========== ============================================
Params	    Type	      Required	  Description
code	      string	    Y	          error code，0 means success
msg         string      Y           error code description
data	      json	      Y	          response data
=========== =========== =========== ============================================

:Data Structure:

===================== =========== =========== ====================================================================================
Params	              Type	      Required	  Description
request_id            String      Y           unique ID for each HTTP request
id                    int         Y           withdrawal record id
uid                   int         Y           user id
symbol                String      Y           symbol name
amount                String      Y           withdrawal amount
withdraw_fee_symbol   String      Y           withdrawal fees symbol
withdraw_fee          String      Y           withdrawal fees
fee_symbol            String      Y           mining symbol
real_fee              String      Y           miner fee
created_at            String      Y           created time
updated_at            String      Y           updated time
address_to            String      Y           withdrawal address
txid                  String      Y           transaction id in blockchain
confirmations         int         Y           confirmations in blockchain
saas_status           int         Y           status of platform review
company_status        int         Y           status of merchant review
status                int         Y           0 Unreviewed, 1 Reviewed，2 Review Rejected，3 Processing，4 failture, 5 complete
===================== =========== =========== ====================================================================================

:Response Samples:

::

	{
		"code": "0",
		"msg": "suc",
		"data": [
			{
				"request_id":"11",
				"id": 123,
				"uid"：2,
				"symbol "："ETH",
				"amount"："0.0002",
				"withdraw_fee_symbol"："BTC"，
				"withdraw_fee"："1"，
				"fee_symbol"：""，
				"real_fee": "0.0000000000000001",
				"created_at":1545273830000,
				"updated_at":1545273830000,
				"address_from"："0x794b0c610e011d0d40c810ef146b4dd989a67152"，
				"address_to": "0x754b0c610e311d0d00c810ef857b4dd989a67162",
				"txid":"78d1edef3b3fd14365f88cf2d03e8c29ec49ac1a43cedde9e21d320b3268f4de",
				"confirmations":11,
				"saas_status":1,
				"company_status":1,
				"status":1
			}
		]
	}
