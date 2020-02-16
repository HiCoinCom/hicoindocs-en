
2.4 Get User Account Information by Symbol and Uid
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:URI: /api/account/getByUidAndSymbol
:Method: GET
:Request Parameters:

=========== =========== =========== =======================================
Params	    Type	      Required 	  Description
uid	        string	    Y	          user id
symbol      string      Y           symbol name
app_id	    string	    Y	          app id
time	      long	      Y	          timestamp
sign	      string	    Y	          sign value
=========== =========== =========== =======================================

:Response Parameters:

================ =========== =========== =======================================
Params	         Type	       Required 	 Description
normal_balance   string      Y           balance of normal account
lock_balance     string      Y           balance of lock account
deposit_address  string      Y           deposit address
================ =========== =========== =======================================

:Response Samples:

::

	{
		"code": "0",
		"msg": "suc",
		"data": {
			"normal_balance ":"32323.233",
			"lock_balance ":"32323.233",
			"deposit_address": "123dsdfe46wefsfsgsdy5teq"
		}
	}
