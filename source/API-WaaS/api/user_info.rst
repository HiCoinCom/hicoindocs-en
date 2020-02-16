
2.3 Querying User's Information
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:URI: api/user/info
:Method:  GET
:Request Parameters:

=========== =========== =========== ======================================================================
Params	    Type        Required	  Description
country     string	    N	          country code, For example, the Chinese country code uses 86
mobile      string      N           phone number
email       string      N           email
app_id      string	    Y	          app id
time        long	      Y	          timestamp
sign        string	    Y	          sign value
=========== =========== =========== ======================================================================

:Response Parameters:

================ =========== =========== =======================================
Params	         Type	       Required	   Description
uid              string      Y           user id
nickname         string      Y           user's nickname
================ =========== =========== =======================================


:Response Samples:

::

	{
	    "code": "0",
	    "msg": "suc",
	    "data": {
	        "uid"：10001,
	        "nickname":"135****7778"
	    }
	}
