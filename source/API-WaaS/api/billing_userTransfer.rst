
2.7 Internal Transfer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:Note: No fees for internal transfers
:URI: /api/billing/userTransfer
:Method: POST
:Request Parameters:

=========== =========== =========== =========================================================
Params	    Type        Required	  Description
request_id  string	    Y	          unique ID for each HTTP request
from_uid    string	    Y	          from user id
to_uid      string	    Y	          to user id
amount      string	    Y	          transfer amount
symbol      string      Y           symbol name
app_id	    string	    Y	          app id
time	      long	      Y	          timestamp
sign	      string	    Y	          sign value
=========== =========== =========== =========================================================

:Response Parameters:

=========== =========== =========== =========================================================
Params	    Type        Required	  Description
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
