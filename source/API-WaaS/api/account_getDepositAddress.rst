
2.6 Get User's Deposit Address
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:URI: /api/account/getDepositAddress
:Method: POST
:Request Parameters:

=========== =========== =========== =======================================
Params	    Type	      Required	  Description
uid	        string	    Y	          user id
symbol      string      Y           symbol name
app_id	    string	    Y	          app id
time	      long	      Y	          timestamp
sign	      string	    Y	          sign value
=========== =========== =========== =======================================

:Response Parameters:

================ =========== =========== =======================================
Params	         Type	       Required 	 Description
uid              int         Y           user id
address          string      Y           deposit address
================ =========== =========== =======================================

:Response Samples:

::

	{
	    "code": "0",
	    "msg": "suc",
	    "data": {
	        "uid":10000,
	        "address": "1PiX4n37tGSf1zXEPpByYZ8m9Z7Rs3GQXZ"
	    }
	}
