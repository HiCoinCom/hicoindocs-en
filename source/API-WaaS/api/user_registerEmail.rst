
2.2 Email Registration Interface
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:URI: api/user/registerEmail
:Method: POST
:Request Parameters:

=========== =========== =========== ============================================================
Params	    Type        Required	  Description
email       string      Y           email
app_id	    string	    Y	          app id
time	      long	      Y	          timestamp
sign	      string	    Y	          sign value
=========== =========== =========== ============================================================

:Response Parameters:

================ =========== =========== =======================================
Params           Type	       Required	   Description
uid              string      Y           user id
================ =========== =========== =======================================


:Response Samples:

::

	{
	    "code": "0",
	    "msg": "suc",
	    "data": {
	        "uid"：10000
	    }
	}
