4.1 Address Registration Interface
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:Description: Push address to the platform, this address is used to assign to users

:Interface Address: /api/v1/address/register
:Request Method: POST
:Note: A maximum of 100 addresses per push to Custody, with each push checking that the number of addresses remaining available to Custody is greater than 5,000 and disallowing registration if 5,000 addresses are not being used. If the address is memo type, only one address needs to be registered, and the memo will be allocated by Party B

:Request Parameters:

========= ========== ============= ==============================================================================
Param	    Type        Required       Description
app_id	  string	   Yes	          Customer ID
time      int64	       Yes	          Timestamp
sign	  string	   Yes	          Use Party A's private key to sign the plaintext MD5 of the requested data
data	  string	   Yes	          Use Party B's public key to encrypt the requested data
========= ========== ============= ==============================================================================

:Data Structure After Request Parameter Data Decryption:

========= ======= ========== =====================================================================
Param      Type     Required   Description
symbol	   string	Yes	     Token name
addresses  string   Yes	     Address list (can be separated by commas, up to 100 at a time)
memo	   bool	    Yes	     Whether it is memo type
========= ======= ========== =====================================================================



:Request Parameters:

========= ======= ========== =================================================================
Param      Type     Required   Description
code      int	    Yes	      Status code
msg       string    Yes        Status information
data	  string	Yes	      Use Party A's public key to encrypt the returned data
sign	  string	Yes	      Use Party B's private key to sign the return data plaintext MD5
========= ======= ========== =================================================================
