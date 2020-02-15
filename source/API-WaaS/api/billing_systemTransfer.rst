
2.8 System Transfer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:URI: /api/billing/systemTransfer
:Method: POST
:Request Parameters:

=========== =========== =========== =========================================================
Params	    Type	      Necessary	  Description
request_id  string	    Y	          unique ID for each HTTP request
to_uid      string	    Y	          user id
amount      string	    Y	          transfer amount
symbol      string      Y           symbol name
app_id	    string	    Y	          app id
time	      long	      Y	          timestamp
sign	      string	    Y	          sign value
=========== =========== =========== =========================================================

:Request Parameters:

=========== =========== =========== =========================================================
Params	    Type	      Necessary	  Description
code	      string	    Y	          error code，0 means success
msg         string      Y           error code description
data	      json	      Y	          response data，status=0->success, status=1->failure
=========== =========== =========== =========================================================

:Response Samples:

::

	{
	    "code": "0",
	    "msg": "suc",
	    "data": {
		    "status": 0
	    }
	}
