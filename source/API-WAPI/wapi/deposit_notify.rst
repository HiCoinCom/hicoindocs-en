4.3 Deposit notification call interface
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


:Description: Deposit notification call interface
:Interface Address: /api/v1/deposit/notify
:Request Method: POST
:Note: 1. For the same txid, different addresses, separate notifications
       2. For the same txid, the same address, and the amount of notification will be cumulative
       3. For the same deposit, please make sure that the request_id remains the same, otherwise it will cause repeated payments
       4. After request decryption, request_id will be included

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
request_id      string       Yes          Unique identifier for a single request
address_from    string       No          from address
address_to      string       Yes          to address
txid            string       Yes          Transaction ID
amount          decimal      Yes          Amount
confirm         int          Yes          Confirmation number
symbol          string       Yes          Token name
balance         decimal      Yes          Hot wallet balance
status          int          Yes          1 =success; 0 = failure
memo            string       No          memo ID
============== ========== ============= ===================================================



:Request Parameters:

========= ======= ========== ===================================================
Param      Type     Required   Description
code      int	    Yes	      Status code
msg       string    Yes        Status information
data	  string	Yes	      Use Party A's public key to encrypt the returned data
sign	  string	Yes	      Use Party B's private key to sign the return data plaintext MD5
========= ======= ========== ===================================================

:The Data Structure After Decryption of the Corresponding Parameter Data:
 "data":  {"request_id":"12345"}
