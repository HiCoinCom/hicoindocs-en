User withdrawal
======================


A withdrawal
------------

:Description: If the withdrawal address is the internal address of the Alliance, it will not be linked; Otherwise, you need to chain up. In addition, in order to avoid illegal withdrawal requests, when the wallet service receives a withdrawal request from a third-party application, it will call the [Withdrawal Reconfirmation Interface] provided by the third party.
:Interface address: /api/v2/billing/withdraw
:Request method: POST
:Request parameters:

========= ========== ============= ============================================================================================================
Param	  type       required      Description
app_id	  String     Optional	   Merchant's unique expression
data      String     Optional      The encrypted string and the decrypted format are defined as follows
========= ========== ============= ============================================================================================================

:Data structure after decryption of request parameter data:

============ ======= ============= =====================================================================================================================================
Param        type    required      Description
time         long    required	   Current timestamp
charset      String  required      Coding format, no special case, transfer parameter UTF-8
version      String  required      Interface version number, no special case, transfer parameter v2
request_id   String  required      Request unique identification, up to 64 bits
from_uid     String  required      Transfer out user ID
to_address   String  required      Transfer in the user address, memo type, use "_" For example:eos_24545
amount       String  required      Withdrawal amount, including withdrawal service charge; The service charge needs to be configured in the background of the merchant
symbol       String  required      Withdrawal currency
============ ======= ============= =====================================================================================================================================


:Example request parameters:

::

	app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=GCJBk77n7epyOexdGZ20qvukd321TpJ62lIAtlCinW6TzHx8SIbm6evXGulO87UgLTzIWCtgupgeLJKDdZmC7msuPNBGK--Ec27WZXjuhI0gNWXcOVk5RW_VRVcyfJ1Ml-DMW8XVxZRgA2U1bt9BztiyfryzMGj8_jl1IXd5sOQfPYXulCdm70WyTJpjsDkuMSov6QUmOn-C_-HUoZ7s715EMeZ60D09uUsF0i6mKLhFZTEQZPGPeJITYSJNddAw7nvqvX2KzNc6YUeCQhEmU1Dfxp65W4e3SVOgpd_2Q-dLN1MpOlkUKwbmbpb-gEh_s68yl7ox6WSgKfCK4i_uvA



:Response parameters:


========= ========== ============= =========================================================================================
Param	  type       required       Description
data      String     Optional       The encrypted string and the decrypted format are defined as follows
========= ========== ============= =========================================================================================


:After the response parameter data is decrypted:

========= ========== ============= ===============================================================================
Param	  type       required      Description
code      String     required      Status code
msg       String     required      Response result description
data      String     Optional      For specific response data, the data structure is defined as follows
========= ========== ============= ===============================================================================



:After the response parameter data is decrypted:

============== ======= ======== ========================================================================================================
param          type    required Description
status         string  required 0 under review by risk control, 1 in payment, 2 audit rejection, 4 failed, 5 success, 6 cancelled , 7 pending KYT verification, 8 pending manual review (KYT risk level too high)
============== ======= ======== ========================================================================================================


:Example response:

::

	{"data":"k4w5AijeFWF3AtYbgP1RYfej7ifW4R663pOt5bhQp8RIxFUVb6zKOy4snKukA_5T9DVwhjdhsHjSRpmxD5LwL2OtplwSUACRPnW39ANypjO5YeMJTpiY9_7jofZWYzAMB4gdkrAI3DAbvkjCFUKQIXfAGMl25sp05mdBZgfY1oEtveSyislYOwaLM3SfN_2bFvrKy7E2V0AkZhrYImKiCzmDZvE-i93cePVQ4ODiuusHgk1vH5QgvPv62Sh-xxQPb4TsWj2G_RBoo9dFlg4zbWOdb9z6SVzR86ouxKOX_RhE4vWsReVD4ukdsW8eO7SVCI74qc61hIS12X6u-Hv40g"}

:Example after response data decryption:


::

	{"code":"0","data":{"id":48680,"status":0},"msg":"success"}





Second confirmation of withdrawal information
------------------------

:Description:  After receiving a withdrawal request, the platform will call the secondary confirmation interface provided by the third party to confirm that the request is a withdrawal request normally initiated by the merchant. This interface only defines the interface specification, the specific interface needs to be implemented by the developer.
:Interface address: The interface address is provided by the developer and can be configured on the platform by contacting the administrator
:Request method: POST
:Request parameters:


========= ========== ============= ======================================================================================================
Param	  type       required      Description
app_id	  String     Optional	   Merchant's unique identification
data      String     Optional	   The encrypted string and the decrypted format are defined as follows
========= ========== ============= ======================================================================================================

:Data structure after decryption of request parameter data:

============== =========== =============== ===================================================================================================================
Param          type        required        Description
time	       long	   required        Current timestamp
charset        String      required        Coding format, no special case, transfer parameter UTF-8
version        String      required        Interface version number, no special case, transfer parameter v2
request_id     String      required        Request unique identity
from_uid       String      required        Transfer out user ID
to_address     String      required        Transfer in user address
amount         String      required        Withdrawal amount, including withdrawal service charge; The service charge needs to be configured in the background of the merchant
symbol         String      required        Withdrawal currency
check_sum      String      required        Random check code. The third party returns this field as it is. The platform considers it successful
============== =========== =============== ===================================================================================================================


:Example request parameters:

::

  app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=UoJC0VeVSvdOCYbkUIQxnJ2k-MINFmdfhHo1bpgK1kqcCKEZ1MtBFmvMnrZsmpQKVyNbFyBmLHzOk_T5FTxKA0VROneKR4wyK0G6HPQM6pDeSz2BPwwaw-2uiBSiPeQEwOabWl0MLyoJyj1g4VLcBgazCYeD5YPJXFOzjAEgkhfbMEcoS1to_ooISnIMeQvhj8g3I3m5k519eJ9KWOv5R3_EGMaI-yLlCB5CIVd4byjnBxDJxsRMR7yuEhIjfvsy49MgglSTrddCFu3ZHNwGlv_DzTJIMhJHRV7z4x8YQV2atP-BBgY9eozPa0JIkjBctdqigvzJs5nsbl76wL5Gv5-icGv4qtOF0w11t0oPi051Y7fiuPJ20BK6GAPEu_HroTvcWh-3vh2_U03Donv306HMvC-vXrQH18TGVqjtOlVhQW_wg4PF9fjMgNCsk3k57vzVfuRruurLv6-FD6HRvoUe4WfgSAi-jMRpuwXC8mL44r-dLDfo4wUdrjEk8tkjSZea8O066bJeVVUU3rD7qqL32Uf-3Bkcy26jsHLf-QK8oYi2xjddd2PSoHnpSIbRdDYrYLdO_zUFZudg4FBHFzQ6sSLesS_jA63xJZS1xk6EjejaSpID3r-7YXDQtM3y5O1TG3URmF5sVbWL5iekubN2jEjkQ2QdV4hz0sBdmlx8GrPUWSnbtLMV7zcxAhyodzIeWeeZCKeu1AF903YJvKZls8eKMEvd__PYSnnRtXVxNUvFFo-GL3sOtDAAhjKdLLSWCVGqDQsKSrORffejbDeHVGsmtFxPC5kvKHLbJvAW6QDzpG8hqmZLrtjxvTmcVMt1_hn9-VSi-qFW8xPorYmF5Hw1G5nZca7NK5k2Qs6xieNgw34Sps-tj38WxhXacRwlEp1Yt3Jj3BlMlxCD9VWxWO17Yvj3MmJTNgf-d22PvPV_mZrJaqjm6BSfuz9DVYVjsIuZF_eOgMaVTm31FFuFZvPF9G_lhC4CQ0Zb5KfpYx0NMJjGfBPtxZ3MsF8H


:Response parameters:

========= ========== ============= ==========================================================================
Param	  type       required      Description
data      String     Optional      The encrypted string and the decrypted format are defined as follows
========= ========== ============= ==========================================================================

:Data structure:

=============== ========= ========== ====================================================
Param           type      required   Description
check_sum       String    required   Check in request parameter check_sum
time            String    Optional   time stamp
=============== ========= ========== ====================================================

:Example response:


::

  {"data":"LK4D5mrtvTubDxCQM4lqyN2h8TTIkEBL_06FrrrzLrImyMO4Yuac-wdbk5VnGVfCKB5EFaUb162xXUJdTHhpA5CGBCAQKl64h_Dt10C-H8KIoap9dZI90qE4f-mAMAyjF1QzKXJ-f-R_3J3bRGqfHFBRXebh08R8MdRDssniopVOhsFUs4gBxUensKas3_ta15eFIqXPjIgJWfYQCD2DUi1gaKgmN-5Q_tgt-qXp5Y2uh3yfM4g4k71Ahyel3G8S_AktbWl2G9wU3cri3ZVQEo0faIpkX_CKsk9V1YoY5yRopvJbxNtkG9lBFxKnureAQo0KP3f1tsIMOzgcyEXPnA"}

:Example after response data decryption:

::

  {"check_sum":"1234","time":"12345678"}




Asynchronous callback notification of user withdrawal
---------------------------------------------------------

:Description: This interface only defines the interface specification, the specific interface needs to be implemented by the developer
:Interface address: The interface address is provided by the developer and can be configured on the platform by contacting the administrator
:Request method: POST
:Request parameters:


========= ========== ============= ===========================================================================
Param	  type       required      Description
app_id	  String     optional	   Merchant's unique identification
data      String     optional	   The encrypted string and the decrypted format are defined as follows
========= ========== ============= ===========================================================================


:Data structure after decryption of request parameter data:

Withdrawal notice：

====================== =========== ============== ===========================================================================================================================
Param	               type        required       Description
charset                String      required       Coding format, no special case, transfer parameter UTF-8
version                String      required       Interface version number, no special case, transfer parameter v2
side                   String      required       Notice type, recharge notice: deposit, withdrawal notice: withdraw
notify_time            String      required       Notice time
request_id             String      required       The withdrawal request_id corresponds to the request in the withdrawal interface id
id                     String      required       Withdrawal ID
uid                    String      required       Withdrawal user ID
symbol                 String      required       currency
amount                 String      required       Withdrawal amount
withdraw_fee_symbol    String      required       Currency of withdrawal service deposit
withdraw_fee           String      required       Service fee for withdrawal
fee_symbol             String      required       Currency of Mining handling charge
real_fee               String      required       Miner's fee
address_to             String      required       Depositing address
created_at             String      required       Creation time
updated_at             String      required       Revision time
txid                   String      required       Blockchain transaction ID
confirmations          String      required       Number of blockchain confirmations
status                 String      required       Withdrawal status: 0 under review by risk control, 1 in payment, 2 audit rejection, 4 failed, 5 success, 6 cancelled , 7 pending KYT verification, 8 pending manual review (KYT risk level too high)
====================== =========== ============== ===========================================================================================================================


:Example request parameters:

::

  app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=UoJC0VeVSvdOCYbkUIQxnJ2k-MINFmdfhHo1bpgK1kqcCKEZ1MtBFmvMnrZsmpQKVyNbFyBmLHzOk_T5FTxKA0VROneKR4wyK0G6HPQM6pDeSz2BPwwaw-2uiBSiPeQEwOabWl0MLyoJyj1g4VLcBgazCYeD5YPJXFOzjAEgkhfbMEcoS1to_ooISnIMeQvhj8g3I3m5k519eJ9KWOv5R3_EGMaI-yLlCB5CIVd4byjnBxDJxsRMR7yuEhIjfvsy49MgglSTrddCFu3ZHNwGlv_DzTJIMhJHRV7z4x8YQV2atP-BBgY9eozPa0JIkjBctdqigvzJs5nsbl76wL5Gv5-icGv4qtOF0w11t0oPi051Y7fiuPJ20BK6GAPEu_HroTvcWh-3vh2_U03Donv306HMvC-vXrQH18TGVqjtOlVhQW_wg4PF9fjMgNCsk3k57vzVfuRruurLv6-FD6HRvoUe4WfgSAi-jMRpuwXC8mL44r-dLDfo4wUdrjEk8tkjSZea8O066bJeVVUU3rD7qqL32Uf-3Bkcy26jsHLf-QK8oYi2xjddd2PSoHnpSIbRdDYrYLdO_zUFZudg4FBHFzQ6sSLesS_jA63xJZS1xk6EjejaSpID3r-7YXDQtM3y5O1TG3URmF5sVbWL5iekubN2jEjkQ2QdV4hz0sBdmlx8GrPUWSnbtLMV7zcxAhyodzIeWeeZCKeu1AF903YJvKZls8eKMEvd__PYSnnRtXVxNUvFFo-GL3sOtDAAhjKdLLSWCVGqDQsKSrORffejbDeHVGsmtFxPC5kvKHLbJvAW6QDzpG8hqmZLrtjxvTmcVMt1_hn9-VSi-qFW8xPorYmF5Hw1G5nZca7NK5k2Qs6xieNgw34Sps-tj38WxhXacRwlEp1Yt3Jj3BlMlxCD9VWxWO17Yvj3MmJTNgf-d22PvPV_mZrJaqjm6BSfuz9DVYVjsIuZF_eOgMaVTm31FFuFZvPF9G_lhC4CQ0Zb5KfpYx0NMJjGfBPtxZ3MsF8H


:Response parameters:

Return string: SUCCESS means SUCCESS, FAILURE means FAILURE (note that the return parameter does not need to be encrypted here)





Synchronize withdrawal records
------------------------

:Description: Batch access to withdrawal records
:The interface address: /api/v2/billing/syncWithdrawList
:Request method: GET
:Request parameters:

========= ========== ============= ====================================================================================================
Param	  type       required      Description
app_id	  string     optional	   Merchant's unique identification
data      string     optional	   The encrypted string and the decrypted format are defined as follows
========= ========== ============= ====================================================================================================

:Data structure after decryption of request parameter data:

========= ======= =========== ============================================================================
Param     type    required    Description
time      long    required    Current timestamp
charset   String  required    Coding format, no special case, transfer parameter UTF-8
version   String  required    Interface version number, no special case, transfer parameter v2
max_id    String  required    Return 100 recharge record data greater than ID
========= ======= =========== ============================================================================


:Example request parameters:

::

	app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=GCJBk77n7epyOexdGZ20qvukd321TpJ62lIAtlCinW6TzHx8SIbm6evXGulO87UgLTzIWCtgupgeLJKDdZmC7msuPNBGK--Ec27WZXjuhI0gNWXcOVk5RW_VRVcyfJ1Ml-DMW8XVxZRgA2U1bt9BztiyfryzMGj8_jl1IXd5sOQfPYXulCdm70WyTJpjsDkuMSov6QUmOn-C_-HUoZ7s715EMeZ60D09uUsF0i6mKLhFZTEQZPGPeJITYSJNddAw7nvqvX2KzNc6YUeCQhEmU1Dfxp65W4e3SVOgpd_2Q-dLN1MpOlkUKwbmbpb-gEh_s68yl7ox6WSgKfCK4i_uvA


:Response parameters:

========= ========== ============= ================================================================================
Param	  type       required       Description
data      String     Optional       The encrypted string and the decrypted format are defined as follows
========= ========== ============= ================================================================================


:After the response parameter data is decrypted:

========= ========== =============== ==========================================================================
Param	  type       required        Description
code	  String     required	     Status code
msg       String     required        Response result description
data      String     Optional        For specific response data, the data structure is defined as follows
========= ========== ============= ==========================================================================


:Data structure:

===================== ========= ========== ========================================================================================================================
Param                 type       required   Description
request_id            String     required   Request ID
id                    int        required   Withdrawal ID
uid                   int        required   Withdrawal user ID
symbol                String     required   currency
amount                String     required   Withdrawal amount
withdraw_fee_symbol   String     required   Currency of withdrawal service deposit
withdraw_fee          String     required   Service fee for withdrawal
fee_symbol            String     required   Currency of Mining handling charge
real_fee              String     required   Miner's fee
created_at            Long       required   Creation time
updated_at            Long       required   Revision time
address_from          String     required   Source address
address_to            String     required   Arrival address
txid                  String     required   Blockchain transaction ID
confirmations         int        required   Number of blockchain confirmations
saas_status           int        required   Platform audit status: 0 not approved, 1 reviewed, 2 rejected
company_status        int        required   Merchant audit status: 0 not approved, 1 reviewed, 2 rejected
status                int        required   Withdrawal status: 0 under review by risk control, 1 in payment, 2 audit rejection, 4 failed, 5 success, 6 cancelled , 7 pending KYT verification, 8 pending manual review (KYT risk level too high)
===================== ========= ========== ========================================================================================================================


:Example response:

::

	{"data":"LK4D5mrtvTubDxCQM4lqyN2h8TTIkEBL_06FrrrzLrImyMO4Yuac-wdbk5VnGVfCKB5EFaUb162xXUJdTHhpA5CGBCAQKl64h_Dt10C-H8KIoap9dZI90qE4f-mAMAyjF1QzKXJ-f-R_3J3bRGqfHFBRXebh08R8MdRDssniopVOhsFUs4gBxUensKas3_ta15eFIqXPjIgJWfYQCD2DUi1gaKgmN-5Q_tgt-qXp5Y2uh3yfM4g4k71Ahyel3G8S_AktbWl2G9wU3cri3ZVQEo0faIpkX_CKsk9V1YoY5yRopvJbxNtkG9lBFxKnureAQo0KP3f1tsIMOzgcyEXPnA"}

:Example after response data decryption:

::

	{
	    "code":"0",
	    "data":[
	        {
	            "withdraw_fee":"0.4",
	            "symbol":"LTC",
	            "amount":"10",
	            "real_fee":"0",
	            "fee":"0",
	            "address_to":"LhFrA5ZJL15UdRV1uEfFxfdqWJUbBhXpRk1",
	            "created_at":1551429063000,
	            "txid":"",
	            "confirmations":0,
	            "address_from":"",
	            "uid":10739,
	            "withdraw_fee_symbol":"ETH",
	            "fee_symbol":"LTC",
	            "saas_status":0,
	            "updated_at":1551429063000,
	            "company_status":0,
	            "id":48393,
	            "request_id":"123",
	            "status":0
	        }
	    ],
	    "msg":"success"
	}





Batch access to withdrawal records
------------------------

:Description: Batch access to withdrawal records
:The interface address: /api/v2/billing/withdrawList
:Request method: GET
:Request parameters:

========= ========== ============= ======================================================================================================
Param	  type       required      Description
app_id	  String     Optional	   Merchant's unique identification
data      String     Optional      The encrypted string and the decrypted format are defined as follows
========= ========== ============= ======================================================================================================

:Data structure after decryption of request parameter data:

========= ========== ============= =================================================================================
Param	  type       required      Description
time      long	     required      Current timestamp
charset   String     required      Coding format, no special case, transfer parameter UTF-8
version   String     required      Interface version number, no special case, transfer parameter v2
ids       String     required      Multiple requests_id are separated by commas, up to 100 requests_id
========= ========== ============= =================================================================================


:Example request parameters:

::

	app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=GCJBk77n7epyOexdGZ20qvukd321TpJ62lIAtlCinW6TzHx8SIbm6evXGulO87UgLTzIWCtgupgeLJKDdZmC7msuPNBGK--Ec27WZXjuhI0gNWXcOVk5RW_VRVcyfJ1Ml-DMW8XVxZRgA2U1bt9BztiyfryzMGj8_jl1IXd5sOQfPYXulCdm70WyTJpjsDkuMSov6QUmOn-C_-HUoZ7s715EMeZ60D09uUsF0i6mKLhFZTEQZPGPeJITYSJNddAw7nvqvX2KzNc6YUeCQhEmU1Dfxp65W4e3SVOgpd_2Q-dLN1MpOlkUKwbmbpb-gEh_s68yl7ox6WSgKfCK4i_uvA


:Response parameters:


========= ========== ============= ===============================================================================
Param	  type       required       Description
data      String     Optional       The encrypted string and the decrypted format are defined as follows
========= ========== ============= ===============================================================================


:After the response parameter data is decrypted:

========= ========== ============= ==================================================================================
Param     type       required      Description
code      String     required	   Status code
msg       String     required      Response result description
data      String     Optional      For specific response data, the data structure is defined as follows
========= ========== ============= ==================================================================================

:Data structure:

===================== ========== ============ =============================================================================================================
Param                 type       required     Description
request_id            String     required     Request ID
id                    int        required     Withdrawal ID
uid                   int        required     Withdrawal user ID
symbol                String     required     currency
amount                String     required     Withdrawal amount
withdraw_fee_symbol   String     required     Currency of withdrawal service deposit
withdraw_fee          String     required     Service fee for withdrawal
fee_symbol            String     required     Currency of Mining handling charge
real_fee              String     required     Miner's fee
created_at            Long       required     Creation time
updated_at            Long       required     Revision time
address_from          String     required     Source address
address_to            String     required     Arrival address
txid                  String     required     Blockchain transaction ID
confirmations         int        required     Number of blockchain confirmations
saas_status           int        required     Platform audit status
company_status        int        required     Merchant audit status
status                int        required     Withdrawal status: 0 under review by risk control, 1 in payment, 2 audit rejection, 4 failed, 5 success, 6 cancelled , 7 pending KYT verification, 8 pending manual review (KYT risk level too high)
===================== ========= ========== =======================================================================================================================


:Example response:

::

	{"data":"LK4D5mrtvTubDxCQM4lqyN2h8TTIkEBL_06FrrrzLrImyMO4Yuac-wdbk5VnGVfCKB5EFaUb162xXUJdTHhpA5CGBCAQKl64h_Dt10C-H8KIoap9dZI90qE4f-mAMAyjF1QzKXJ-f-R_3J3bRGqfHFBRXebh08R8MdRDssniopVOhsFUs4gBxUensKas3_ta15eFIqXPjIgJWfYQCD2DUi1gaKgmN-5Q_tgt-qXp5Y2uh3yfM4g4k71Ahyel3G8S_AktbWl2G9wU3cri3ZVQEo0faIpkX_CKsk9V1YoY5yRopvJbxNtkG9lBFxKnureAQo0KP3f1tsIMOzgcyEXPnA"}

:Example after response data decryption:

::

	{
	    "code":"0",
	    "data":[
	        {
	            "withdraw_fee":"0.4",
	            "symbol":"LTC",
	            "amount":"10",
	            "real_fee":"0",
	            "fee":"0",
	            "address_to":"LhFrA5ZJL15UdRV1uEfFxfdqWJUbBhXpRk1",
	            "created_at":1551429063000,
	            "txid":"",
	            "confirmations":0,
	            "address_from":"",
	            "uid":10739,
	            "withdraw_fee_symbol":"ETH",
	            "fee_symbol":"LTC",
	            "saas_status":0,
	            "updated_at":1551429063000,
	            "company_status":0,
	            "id":48393,
	            "request_id":"123",
	            "status":0
	        }
	    ],
	    "msg":"success"
	}
