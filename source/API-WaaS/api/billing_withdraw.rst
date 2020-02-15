
2.9 Withdrawal interface
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
:Note: If to_address is an internal address, the withdrawal interface functions the same as the internal transfer interface.
:URI: /api/billing/withdraw
:Method: POST
:Request Parameters:

=========== =========== =========== =========================================================
Params	    Type	      Necessary	  Description
request_id  string	    Y	          unique ID for each HTTP request
from_uid    string	    Y	          from user id
to_address  string	    Y	          withdrawal address
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

:Data Structure:

============== ======= =========== =================================================
Params         Type    Necessary   Description
status         string  Y           explained as follows
withdraw_type  int     Y           1: withdraw, 2:Internal Transfer
============== ======= =========== =================================================

**Note:**

withdraw_type=1, status: 0 Unreviewed, 1 Reviewed，2 Review Rejected，3 Processing，4 failture, 5 complete
withdraw_type=2, status: 0 success, 1 failture

:Response Samples:

::

	{
	    "code": "0",
	    "msg": "suc",
	    "data": {
		    "statuts": 0
				"withdraw_type":1
	    }
	}
