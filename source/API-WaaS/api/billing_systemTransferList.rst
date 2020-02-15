
2.15 Batch Get System Transfer Records
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:URI: /api/billing/systemTransferList
:Method: GET
:Request Parameters:

=========== =========== =========== ===================================================================================
Params	    Type	      Necessary	  Description
ids	        string	    Y	          multiple 'request_id' are separated by commas, up to 100 request_id
app_id	    string	    Y	          app id
time	      long	      Y	          timestamp
sign	      string	    Y	          sign value
=========== =========== =========== ===================================================================================

:Request Parameters:

=========== =========== =========== ============================================
Params	    Type	      Necessary	  Description
code	      string	    Y	          error code，0 means success
msg         string      Y           error code description
data	      json	      Y	          response data
=========== =========== =========== ============================================

:Data Structure:

===================== =========== ============ =================================================
Params                Type        Necessary    说明
request_id            String      Y            unique ID for each HTTP request
id                    int         Y             system transfer id
symbol                String      Y            symbol name
amount                String      Y            deposit amount
created_at            String      Y            created time
updated_at            String      Y            updated time
from_uid              int         Y            from uid
to_uid                int         Y            to uid
status                int         Y            0:success, 1:failure
===================== =========== ============ =================================================


:Response Samples:

::

	{
		"code": "0",
		"msg": "suc",
		"data":[
			{
				"request_id":"11",
				"id": 1,
				"symbol" ："ETH",
				"amount"："0.0002000000000000",
				"created_at": 1545273830000,
				"updated_at":1545273830000,
				"from_uid": 10001,
				"to_uid": 10000,
				"status": "1"
			}
		]
	}
