
3.2 The number of remaining addresses available interface
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:Description: How many addresses are available in the pushed addresses
:Interface Address: /api/v1/address/available
:Request Method: POST
:Note: It is recommended that the script monitor the available quantity

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
symbol	   string	Yes	     Token Name
========= ======= ========== ===================================================



:Request Parameters:

========= ======= ========== ===================================================
Param      Type     Required   Description
code      int	    Yes	      Status code
msg       string    Yes        Status information
data	  string	Yes	      Use Party A's public key to encrypt the returned data
sign	  string	Yes	      Use Party B's private key to sign the return data plaintext MD5
========= ======= ========== ===================================================

:The Data Structure After Decryption of the Corresponding Parameter Data:

========= ======= ========== ===================================================
Param      Type     Required   Description
symbol	   string	Yes	     Token Name
count	   int	    Yes	     Number of addresses available
========= ======= ========== ===================================================
