3.7 Withdraw Token and Return Interface
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:Description: Push address to the platform, this address is used to assign to users

:Interface Address: /api/v1/withdraw/cancel
:Request Method: POST
:Note: Called when the withdrawal information is abnormal (address error, token error) and need to be called back

:Request Parameters:

========= ========== ============= ===================================================
Param	    Type        Required       Description
app_id	  string	   Yes	          Customer ID
time      int64	       Yes	          Timestamp
sign	  string	   Yes	          Use Party A's private key to sign the plaintext MD5 of the requested data
data	  string	   Yes	          Use Party B's public key to encrypt the requested data
========= ========== ============= ===================================================

:Data Structure After Request Parameter Data Decryption:

========= ======= ========== ===================================================
Param      Type     Required   Description
symbol	   string	Yes	      Token Name
trans_id   int64    Yes	      Withdrawal ID
msg        string	Yes	      Call back reason
========= ======= ========== ===================================================


:Request Parameters:

========= ======= ========== ===================================================
Param      Type     Required   Description
code      int	    Yes	      Status Code
msg       string    Yes        Status Information
data	  string	Yes	      Use Party A's public key to encrypt the returned data
sign	  string	Yes	      Use Party B's private key to sign the return data plaintext MD5
========= ======= ========== ===================================================

:Example of Successful Response:

::

  {"code": "0","msg": "success","sign": "","data": ""}


:Example of Failure Response:

::

  {"code": "error code","msg": "error message","sign": "","data": ""}
