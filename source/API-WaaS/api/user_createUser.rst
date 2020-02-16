
2.1 Phone Registration Interface
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:URI: api/user/createUser
:Method: POST
:Request Parameters:

=========== =========== =========== ============================================================
Params	    Type        Required	  Description
country	    string	    Y	          country code, For example, the Chinese country code uses 86
mobile      string      Y           phone number
app_id	    string	    Y	          app id
time	      long	      Y	          timestamp
sign	      string	    Y	          sign value
=========== =========== =========== ============================================================

:Response Parameters:

================ =========== =========== =======================================
Params	         Type        Required 	 Description
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
