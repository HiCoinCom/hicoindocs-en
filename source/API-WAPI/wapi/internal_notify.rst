4.6 Internal Notification Interface
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:Description: Internal Notification Interface
:Interface address: /api/v1/internal/notify
:Request method: POST
:Note: This interface is called during transactions that consume miner fees except for cash withdrawal, mainly for deduction of miner fees, such as collection, transfer to cold wallet, etc.

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
address_from    string       No            from address
address_to      string       Yes            to address
txid            string       Yes            Transaction ID
amount          decimal      Yes            Amount
fee             decimal      Yes            Real miner fees
confirm         int          Yes            Confirmation Number
symbol          string       Yes            Token Name
balance         decimal      Yes            Hot wallet balance
memo            string       No            to address memo ID
============== ========== ============= ===================================================



:Request Parameters:

========= ======= ========== ===================================================
Param      Type     Required   Description
code      int	    Yes	      Status Code
msg       string    Yes        Status Information
data	  string	Yes	      Use Party A's public key to encrypt the returned data
sign	  string	Yes	      Use Party B's private key to sign the return data plaintext MD5
========= ======= ========== ===================================================
