
2.5 Get All Account Information of a User
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:URI: /api/account/getAllAccount
:Method: GET
:Request Parameters:

=========== =========== =========== =======================================
Params	    Type	      Required	  Description
uid	        string	    Y	          user id
app_id	    string	    Y	          app id
time	      long	      Y	          timestamp
sign	      string	    Y	          sign value
=========== =========== =========== =======================================

:Response Parameters:

================ =========== =========== =======================================
Params	         Type	       Required 	 Description
symbol           string      Y           symbol name
normal_balance   string      Y           balance of normal account
lock_balance     string      Y           balance of lock account
================ =========== =========== =======================================

:Response Samples:

::

	{
	  "code": "0",
	  "msg": "suc",
	  "data":[
	      {
	        "symbol": "BTC",
	        "normal_balance": "1.00211211",
	        "lock_balance": "0.00211002"
	      },
	      {
	        "symbol": "ETH",
	        "normal_balance": "1.00211211",
	        "lock_balance": "0.00211002"
	      }
	  ]
	}
