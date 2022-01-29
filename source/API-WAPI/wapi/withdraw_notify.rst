4.5 Withdrawal Notification Interface
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:Description: Call interface for withdrawal notification
:Interface Address: /api/v1/withdraw/notify
:Request Method: POST
:Note: 1. The same txid, different addresses, separate notifications
       2. The same txid, the same address, and the amount of notification will be cumulative
       3.	For the same deposte, please make sure that the request_id remains the same, otherwise it will cause repeated payments
       4.	After request decryption, request_id will be included


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
address_from    string         No            from address
address_to      string         Yes            to address
txid            string         Yes            Transaction ID
trans_id        int            Yes            Withdrawal ID
amount          decimal        Yes            Amount
fee             decimal        Yes            Real miner fees
confirm         int            Yes            Confirm the number. When the confirm passes 0, the status of the withdrawal record will be changed to "Paying", and the withdrawal record will not be repeatedly obtained through the /api/v1/withdraw/consume interface
symbol          string         Yes            Token Name
balance         decimal        Yes            Hot Wallet Balance
memo            string         No            to address memo ID
============== ========== ============= ===================================================



:Response Parameters:

========= ======= ========== ===================================================
Param      Type     Required   Description
code      int	    Yes	      Status Code
msg       string    Yes        Status Information
data	  string	Yes	      Use Party A's public key to encrypt the returned data
sign	  string	Yes	      Use Party B's private key to sign the return data plaintext MD5
========= ======= ========== ===================================================
