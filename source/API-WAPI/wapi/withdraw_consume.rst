4.4 Withdrawal Interface
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


:Description: Withdrawal Interface
:Interface Address: /api/v1/withdraw/consume
:Request method: POST
:Note:  This interface can return the latest 20 data at most at a time


:Request Parameters:

========= ========== ============= ===================================================
Param	    Type        Required       Description
app_id	  string	   Yes	          Customer ID
time      int64	       Yes	          Timestamp
sign	  string	   Yes	          Use Party A's private key to sign the plaintext MD5 of the requested data
data	  string	   Yes	          Use Party B's public key to encrypt the requested data
========= ========== ============= ===================================================

:Data Structure After Request Parameter Data Decryption:

============== ========== ============= ===================================================
Param	        Type         Required       Description
symbol          string       Yes          Token Name
============== ========== ============= ===================================================



:Response Parameters:

========= ======= ========== ===================================================
Param      Type     Required   Description
code      int	    Yes	      Status ID
msg       string    Yes        Status information
data	  string	Yes	      Use Party A's public key to encrypt the returned data
sign	  string	Yes	      Use Party B to return the signature of the data plaintext MD5 to the private key
========= ======= ========== ===================================================

:The Data Structure After Decryption of the Corresponding Parameter Data:

"data": [{"trans_id": 1,"symbol": "BTC","amount": 1.43232,"fee": 0.001,"address_to": "3D2oetdNuZUqQHPJmcMDDHYoqkyNVsFk9r"}]

=========== ========= =========== ===================================================
Param        Type      Required      Description
trans_id     string	  Yes	         Withdrawal ID
symbol	     string	  Yes	         Token name
address_to   string	  Yes	         Withdrawal to account address
amount	     decimal	  Yes	         Withdrawal Amount
memo	     string	  No	         Withdraw memo
=========== ========= =========== ===================================================
