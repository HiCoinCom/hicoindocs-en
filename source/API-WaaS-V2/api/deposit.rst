User deposit
======================


Synchronize deposit records
~~~~~~~~~~~~~~~~~~~~~~~~

:Description: Synchronized deposit records
:The interface address: /api/v2/billing/syncDepositList
:Request method: GET
:Request parameters:


========= ========== ============= =======================================================
Param	  type       required      Description
app_id	  String     optional	   merchant unique identifier
data      String     optional	   encrypted String decrypted format defined as follows:
========= ========== ============= =======================================================

:Data structure after decryption of request parameter data:

========= ========== ============= =============================================================
Param	  type       required      Description
time	  long	     required	   current timestamp
charset   String     required      encoding format, no special case, pass parameter UTF-8
version   String     required      interface version number, no special case, pass parameter v2
max_id	  int	     required	   returns 100 records greater than id
========= ========== ============= =============================================================


:Example request parameters:

::

	app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=9fEODHjOOQ1vKGv4nm_EqWrE62XQOr5cFFYOC3Cr-v5d26MLpI7v4ymRFkANT64d5mjIXjkVj6qwrf4PeUbO3rTiRpKPGIQhyoZyR7QTBuv6A4CgxlVl_A2dNy_DZO_cGUNsRyyzUkf0uuuykhDtmBZg6o1oYA1OEWxZdexwjpnn8NSWB4WbPgntZKstbjpAW7xJR6HXekRf4CoEDjuKSYwhs08rk6HiB08Vx6x1KvG_0neBq7Z0hsSHxYKjrQTm9VQLeH5qsXtqPGk07RLHHY_EiT9Uh9hTC5xWx7uq70CsJ9GGIs9ZenQh-dda6gmNecgs94-qsZVUkfkSL07kTg


:Response parameters:


========= ========== ============= ========================================================
Param	  type       required      Description
data      String     optional      encrypted String decrypted format defined as follows:
========= ========== ============= ========================================================


:After the response parameter data is decrypted:

========= ========== ============= =================================================================
Param	  type       required      Description
code	  String     required	   status code
msg       String     required      the description of the response result
data      String     optional      specific response data the data structure is defined as follows:
========= ========== ============= =================================================================


:Data structure:


===================== ========== =========== =================================================
Param                 type       required    Description
id                    int        required    deposit unique id
uid                   int        required    deposit user id
symbol                String     required    currency
amount                String     required    deposit amount
created_at            Long       required    creation time
updated_at            Long       required    change time
txid                  String     required    blockchain transaction ID
confirmations         int        required    number of blockchain confirmations
address_to            String     required    depositing account address
status                int        required    0 to be confirmed, 1 success, 2 failed, 4 pending KYT verification, 5 pending manual review (KYT risk level too high), 6 Pending manual review (KYT Deposit Circuit Breaker)
===================== ========== =========== =================================================



:Example response:

::

	{"data":"T1IaOzF2XfNaAOb3XqSFxCq6nu45SpiD9anDIlxHda_lOwX2kNNAl84OOsVnAsMg4IBQICD6_PMglpU5InzL_Q1AoNf_l1kPlk_fMXvmpEz25OAVJ499UYmBpH83TQclFfsxPKaFhIgeNGYgVGaS3BdT4Z0EBmfbMAz9aTa4n5z9Ns4q4b6En030GLINhC8PmaEQ5PDq5ZXZTKiKSrRNpNRi3_FR8hdIJGOLFU6t1Yb2nxqB1D-fY6eRtSHQnCCyas73kj-_kAhyW4dGss7vqKQZPmDe38qSYPrQUoDlJgK_8aCKG8fvJmoC9s3-o3InALAGp3yOawn32E1AxZtNbDQcUux6xbyAhhIOBhyN_V2LPR9yOtJQvm3XbdMxk58i-Y6oZl_YtBdfRncvhDJnAPqP3MN4sdbuC3JaC19bKikTDykXzFgD2_rHN4CO8QHUAefRAm-x9hj_sHFOwrJdL9g1H2Auzz1cES4zcp5RKHsduFnUNlvoKRNl9SUuIbDahTtBHlF1Gw9xy1my9KMB2X-u1vvnL83hvp4Rqnz0SyMfnpEnqRph43cCiyj7Ii3cf-Ai8h2i-5yIqr2qDKJoL5GqaOu6hr5atO4IZXZPzY175wZ4nNpCueBXRHoWB2foVmLu_F6xwq06XKDR9U5JYln3iol9DX2OhqM0Bs8cPqw"}

:Example after response data decryption:


::

	{
	    "code":"0",
	    "data":[
	        {
	            "withdraw_fee":"0",
	            "symbol":"BTC",
	            "amount":"0.0001",
	            "real_fee":"0",
	            "fee":"0",
	            "address_to":"1CfYiePwcf3mWhLBQH2ac35C7jmE2udQqH",
	            "created_at":1539050731000,
	            "txid":"",
	            "confirmations":0,
	            "address_from":"",
	            "uid":10596,
	            "withdraw_fee_symbol":"BTC",
	            "fee_symbol":"BTC",
	            "saas_status":0,
	            "updated_at":1543483252000,
	            "company_status":2,
	            "id":45325,
	            "request_id":"",
	            "status":2
	        },
	        {
	            "withdraw_fee":"0.0000001",
	            "symbol":"BTC",
	            "amount":"0.0001",
	            "real_fee":"0",
	            "fee":"0.0000001",
	            "address_to":"17m2GM8aRrrnxPt5JhYPJd4qUFqF8rJDop",
	            "created_at":1539065092000,
	            "txid":"",
	            "confirmations":0,
	            "address_from":"",
	            "uid":10595,
	            "withdraw_fee_symbol":"BTC",
	            "fee_symbol":"BTC",
	            "saas_status":1,
	            "updated_at":1543851222000,
	            "company_status":2,
	            "id":45332,
	            "request_id":"",
	            "status":2
	        }
	    ],
	    "msg":"success"
	}





Batch access depositing records
~~~~~~~~~~~~~~~~~~~~~~~~

:Description: Batch access recharge records
:The interface address: /api/v2/billing/depositList
:Request method: GET
:Request method:

========= ========== ============= ========================================================
Param	  type       required      Description
app_id	  String     optional	   merchant unique identifier
data      String     optional	   encrypted String decrypted format defined as follows:
========= ========== ============= ========================================================

:Data structure after decryption of request parameter data:

========= ======= ========== ================================================================
Param     type    required   Description
time      long    required   current timestamp
charset   String  required   encoding format, no special case, pass parameter UTF-8
version   String  required   interface version number, no special case, pass parameter v2
ids       String  required   multiple top-up IDs separated by commas, up to 100 IDs
========= ======= ========== ================================================================

::

	app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=L-GwqoS2NJAOIUHMM5NAqJJvBKxWLjANyh1UHRvQbFUCHfzJBxEpGi514sI_J051wO4QMK9xeZK6_f7p_CIQfVJ7kiq7FNmflHnyjPT9tGdL6h7GSnHcPFEUUyHA7hJlvt3BtPyYuaEN9s1cJ1c8DzlOLTnzRF5EiPPrw-Yq0wtBYORIjEtfOBEMChF5vxu-FIjb3Nx4usIeWEamkC5WpkjRcjPZlE7-pRnA59fgHMtA3-hvsxJYwhCKLFkq-fAPfpTf4IpgZWdmrCEfGAdExSDCoQVNEJZgZnonzy5bDsUBQIRWuJZbO5u0JYnjdBliqpOi_L6j_chbe_er2eT5_w



:Response parameters:

========= ========== ============= ====================================================================
Param	  type       required      Description
data      String     optional      encrypted String decrypted format defined as follows:
========= ========== ============= ====================================================================


:After the response parameter data is decrypted:

========= ========== ============= ======================================================================
Param	  type       required      Description
code	  String     required	   status code
msg       String     required      the description of the response result
data      String     optional      the specific response data the data structure is defined as follows:
========= ========== ============= ======================================================================


:Data structure:

=============== ========= ========== ====================================================
Param            type     required   Description
id               int      required   depositing unique id
uid              int      required   depositing user id
symbol           String   required   currency
amount           String   required   depositing amount
created_at       Long     required   create time, timestamp
updated_at       Long     required   change time, timestamp
txid             String   required   blockchain transaction ID
confirmations    int      required   number of blockchain confirmations
address_to       String   required   depositing account address
status           int      required   0 to be confirmed, 1 success, 2 failed, 4 pending KYT verification, 5 pending manual review (KYT risk level too high), 6 Pending manual review (KYT Deposit Circuit Breaker)
=============== ========= ========== ====================================================


:Example response:

::

	{"data":"T1IaOzF2XfNaAOb3XqSFxCq6nu45SpiD9anDIlxHda_lOwX2kNNAl84OOsVnAsMg4IBQICD6_PMglpU5InzL_Q1AoNf_l1kPlk_fMXvmpEz25OAVJ499UYmBpH83TQclFfsxPKaFhIgeNGYgVGaS3BdT4Z0EBmfbMAz9aTa4n5z9Ns4q4b6En030GLINhC8PmaEQ5PDq5ZXZTKiKSrRNpNRi3_FR8hdIJGOLFU6t1Yb2nxqB1D-fY6eRtSHQnCCyas73kj-_kAhyW4dGss7vqKQZPmDe38qSYPrQUoDlJgK_8aCKG8fvJmoC9s3-o3InALAGp3yOawn32E1AxZtNbDQcUux6xbyAhhIOBhyN_V2LPR9yOtJQvm3XbdMxk58i-Y6oZl_YtBdfRncvhDJnAPqP3MN4sdbuC3JaC19bKikTDykXzFgD2_rHN4CO8QHUAefRAm-x9hj_sHFOwrJdL9g1H2Auzz1cES4zcp5RKHsduFnUNlvoKRNl9SUuIbDahTtBHlF1Gw9xy1my9KMB2X-u1vvnL83hvp4Rqnz0SyMfnpEnqRph43cCiyj7Ii3cf-Ai8h2i-5yIqr2qDKJoL5GqaOu6hr5atO4IZXZPzY175wZ4nNpCueBXRHoWB2foVmLu_F6xwq06XKDR9U5JYln3iol9DX2OhqM0Bs8cPqw"}

:Example after response data decryption:


::

	{
  	"code": "0",
		"msg": "suc",
		"data": [
			{
				"id" ：1,
  			"uid" ：11,
  			"symbol"："ETH",
  			"amount"："0.0002000000000000",
  			"created_at": 1545273830000,
  			"updated_at": 1545273830000,
  			"txid":"78d1edef3b3fd14365f88cf2d03e8c29ec49ac1a43cedde9e21d320b3268f4de",
				"confirmations":11,
  			"status":1,
  			"address_to":"0xcb03bfdccb50c9f62ec1c728f264bf453e037132"
			},
  		{
  			"id" ：2,
  			"uid" ：12,
				"symbol" ："ETH",
  			"amount"："0.0002000000000000",
  			"created_at": 1545273830000,
  			"updated_at": 1545273830000,
  			"txid":"0xd609e050c3d573fb715431edbd36cc08eaa475f813de921026a65c0a96e8113e",
				"confirmations":11,
  			"status":1,
  			"address_to":"0xcb03bfdccb50c9f62ec1c728f264bf453e037132"
  		}
		]
	}






Nonsync callback notification for user deposit
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:Description: This interface only defines the interface specification, the specific interface needs to be implemented by the developer
:Interface address: The interface address is provided by the developer and can be configured on the platform by contacting the administrator
:Request method: POST
:Request parameters:


========= ========== ============= ===========================================================
Param	  type       required      Description
app_id	  String     optional	   merchant unique identifier
data      String     optional	   encrypted String decrypted format is defined as follows:
========= ========== ============= ===========================================================


:Data structure after decryption of request parameter data:

Deposit Notice：

=====================  ========= ============= =====================================================================================
Param	               type      required      Description
charset                String    required      the encoding format, no special case, pass the argument UTF-8
version                String    required      the interface version number, no special case, pass the parameter v2
side                   String    required      notification type, recharge notice: deposit, withdrawal notice: withdraw
notify_time            string    required      the notification time
id                     string    required      the depositing ID
uid                    string    required      the withdrawing user ID
symbol                 string    required      currency
amount                 string    required      the withdrawal amount
address_to             string    required      the depositing address
created_at             string    required      the creation time
updated_at             string    required      the change time
txid                   string    required      blockchain transaction ID
confirmations          string    required      the number of blockchain confirmations
status                 string    required      the depositing status 0 to be confirmed, 1 success, 2 failed, 4 pending KYT verification, 5 pending manual review (KYT risk level too high), 6 Pending manual review (KYT Deposit Circuit Breaker)
===================== ========== ============= =====================================================================================



:Example request parameters:

::

  app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=UoJC0VeVSvdOCYbkUIQxnJ2k-MINFmdfhHo1bpgK1kqcCKEZ1MtBFmvMnrZsmpQKVyNbFyBmLHzOk_T5FTxKA0VROneKR4wyK0G6HPQM6pDeSz2BPwwaw-2uiBSiPeQEwOabWl0MLyoJyj1g4VLcBgazCYeD5YPJXFOzjAEgkhfbMEcoS1to_ooISnIMeQvhj8g3I3m5k519eJ9KWOv5R3_EGMaI-yLlCB5CIVd4byjnBxDJxsRMR7yuEhIjfvsy49MgglSTrddCFu3ZHNwGlv_DzTJIMhJHRV7z4x8YQV2atP-BBgY9eozPa0JIkjBctdqigvzJs5nsbl76wL5Gv5-icGv4qtOF0w11t0oPi051Y7fiuPJ20BK6GAPEu_HroTvcWh-3vh2_U03Donv306HMvC-vXrQH18TGVqjtOlVhQW_wg4PF9fjMgNCsk3k57vzVfuRruurLv6-FD6HRvoUe4WfgSAi-jMRpuwXC8mL44r-dLDfo4wUdrjEk8tkjSZea8O066bJeVVUU3rD7qqL32Uf-3Bkcy26jsHLf-QK8oYi2xjddd2PSoHnpSIbRdDYrYLdO_zUFZudg4FBHFzQ6sSLesS_jA63xJZS1xk6EjejaSpID3r-7YXDQtM3y5O1TG3URmF5sVbWL5iekubN2jEjkQ2QdV4hz0sBdmlx8GrPUWSnbtLMV7zcxAhyodzIeWeeZCKeu1AF903YJvKZls8eKMEvd__PYSnnRtXVxNUvFFo-GL3sOtDAAhjKdLLSWCVGqDQsKSrORffejbDeHVGsmtFxPC5kvKHLbJvAW6QDzpG8hqmZLrtjxvTmcVMt1_hn9-VSi-qFW8xPorYmF5Hw1G5nZca7NK5k2Qs6xieNgw34Sps-tj38WxhXacRwlEp1Yt3Jj3BlMlxCD9VWxWO17Yvj3MmJTNgf-d22PvPV_mZrJaqjm6BSfuz9DVYVjsIuZF_eOgMaVTm31FFuFZvPF9G_lhC4CQ0Zb5KfpYx0NMJjGfBPtxZ3MsF8H


:Response parameters:

Return string: SUCCESS means SUCCESS, FAILURE means FAILURE (note that the return parameter does not need to be encrypted here)


Collect miner fees
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:Description: The currency of account type needs to be collected after recharging. UTXO has no fees for collecting miners' fees
:The interface address: /api/v2/billing/syncMinerFeeList
:Request method: GET
:Request parameters:


========= ========== ============= =======================================================================
Param	  type       repuired      Description
app_id	  String     optional	   Merchant's unique identification
data      String     optional	   The encrypted string and the decrypted format are defined as follows:
========= ========== ============= =======================================================================


:Data structure after decryption of request parameter data:


===================== ========== ============= ===================================================================
Param	              type       repuired      Description
time                  long       repuired      Current timestamp
charset               String     repuired      Coding format, no special case, transfer parameter UTF-8
version               String     repuired      Interface version number, no special case, transfer parameter v2
max_id                int        repuired      Return the data of 100 collected miner fee records greater than ID
===================== ========== ============= ===================================================================



:Example request parameters:

::

  app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=L-GwqoS2NJAOIUHMM5NAqJJvBKxWLjANyh1UHRvQbFUCHfzJBxEpGi514sI_J051wO4QMK9xeZK6_f7p_CIQfVJ7kiq7FNmflHnyjPT9tGdL6h7GSnHcPFEUUyHA7hJlvt3BtPyYuaEN9s1cJ1c8DzlOLTnzRF5EiPPrw-Yq0wtBYORIjEtfOBEMChF5vxu-FIjb3Nx4usIeWEamkC5WpkjRcjPZlE7-pRnA59fgHMtA3-hvsxJYwhCKLFkq-fAPfpTf4IpgZWdmrCEfGAdExSDCoQVNEJZgZnonzy5bDsUBQIRWuJZbO5u0JYnjdBliqpOi_L6j_chbe_er2eT5_w


:Response parameters:

========= ========== ============= ===================================================================================
Param	  type       repuired      Description
data      String     optional      The encrypted string and the decrypted format are defined as follows
========= ========== ============= ===================================================================================


:After the response parameter data is decrypted:

========= ========== ============= ==========================================================================
Param	  type       repuired      Description
code      String     repuired	   Status code
msg       String     repuired      Response result description
data      String     optional      For specific response data, the data structure is defined as follows
========= ========== ============= ==========================================================================

:Data structure:

================== ========== ============= ===================================================
Param              type        repuired     Description
id                 int         repuired     Collect unique ID
symbol             String      repuired     currency
amount             String      repuired     Collection amount
fee                String      repuired     Collection fee
created_at         Long        repuired     Creation time
updated_at         Long        repuired     Revision time
txid               String      repuired     Blockchain transaction ID
confirmations      int         repuired     Number of blockchain confirmations
status             int         repuired     0 to be confirmed, 1 success, 2 failed, 4 pending KYT verification, 5 pending manual review (KYT risk level too high), 6 Pending manual review (KYT Deposit Circuit Breaker)
address_to         String      repuired     depositing to account address
address_from       String      repuired     depositing sending address
txid_type          String      repuired     0 chain transaction, 1 union transfer transaction
base_symbol        String      repuired     Name of main chain currency
contract_address   String      repuired     Currency contract address
email              String      repuired     email
================== ========== ============= ===================================================



:Example response:

::

                                                                                                 {“data”:”T1IaOzF2XfNaAOb3XqSFxCq6nu45SpiD9anDIlxHda_lOwX2kNNAl84OOsVnAsMg4IBQICD6_PM glpU5InzL_Q1AoNf_l1kPlk_fMXvmpEz25OAVJ499UYmBpH83TQclFfsxPKaFhIgeNGYgVGaS3BdT4Z0EBm fbMAz9aTa4n5z9Ns4q4b6En030GLINhC8PmaEQ5PDq5ZXZTKiKSrRNpNRi3_FR8hdIJGOLFU6t1Yb2nxqB1D -fY6eRtSHQnCCyas73kj-_kAhyW4dGss7vqKQZPmDe38qSYPrQUoDlJgK_8aCKG8fvJmoC9s3-o3InAL AGp3yOawn32E1AxZtNbDQcUux6xbyAhhIOBhyN_V2LPR9yOtJQvm3XbdMxk58i-Y6oZl_YtBdfRncvhDJ nAPqP3MN4sdbuC3JaC19bKikTDykXzFgD2_rHN4CO8QHUAefRAm-x9hj_sHFOwrJdL9g1H2Auzz1cES4zc p5RKHsduFnUNlvoKRNl9SUuIbDahTtBHlF1Gw9xy1my9KMB2X-u1vvnL83hvp4Rqnz0SyMfnpEnqRph43cCi yj7Ii3cf-Ai8h2i-5yIqr2qDKJoL5GqaOu6hr5atO4IZXZPzY175wZ4nNpCueBXRHoWB2foVmLu_F6xwq06 XKDR9U5JYln3iol9DX2OhqM0Bs8cPqw”}


:Example after response data decryption:

::

  { "code":"0",
    "data":[
           {
           "id":1,
            "symbol":"BTC",
            "amount":"11",
            "fee":"0.00111",
            "created_at":1539050731000,
            "updated_at":1543483252000,
            "txid":"",
            "confirmations":0,
            "status":2,
            "address_from":"",
            "address_to":"",
            "txid_type":"1",
            "base_symbol":"",
            "contract_address":"123",
            "email":""
            }
       ],
    "msg": "success"
    }
