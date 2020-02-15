
2.10 Get a List of Supported Coins
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:URI: /api/user/getCoinList
:Method: GET
:Request Parameters:

=========== =========== =========== =======================================
Params	    Type	      Necessary	  Description
uid	        string	    Y	          user id
app_id	    string	    Y	          app id
time	      long	      Y	          timestamp
sign	      string	    Y	          sign value
=========== =========== =========== =======================================

:Request Parameters:

=========== =========== =========== ============================================
Params	    Type	      Necessary	  Description
code	      string	    Y	          error code，0 means success
msg         string      Y           error code description
data	      json	      Y	          response data
=========== =========== =========== ============================================

:Response Samples:


::

	{
	    "code": "0",
	    "msg": "suc",
	    "data": [
	        {
	            "symbol"："BTC"
	            "icon": "https://hicoinvip.oss-cn-beijing.aliyuncs.com/saas/1547519554925.png"
	       }
	    ]
	}
