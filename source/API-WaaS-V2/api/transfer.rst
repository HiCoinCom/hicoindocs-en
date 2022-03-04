Merchants bank transfer
======================


Custody Merchant Transfer
~~~~~~~~~~~~~~~~~~~~~~~~

:Description: Custody internal merchants transfer money to each other
:Interface address: /api/v2/account/transfer
:Request method: POST
:Request parameters:


========= ========== ============= =====================================================================
Param	    type       required      Description
app_id	  String	   Optional	     Merchant's unique identification
data      String	   Optional	     The encrypted string and the decrypted format are defined as follows
========= ========== ============= =====================================================================

:Data structure after decryption of request parameter data:

============ =========== ============= =====================================================================
Param         type        required     Description
time          Long        required     Current timestamp
charset       String      required     Coding format, no special case, transfer parameter UTF-8
version       String      required     Interface version number, no special case, transfer parameter v2
request_id    String      required     Request unique identification, up to 64 bits
symbol        String      required     Transfer currency, Custody get currency name
amount        String      required     Transfer quantity, including transfer fees
to            String      required     Transfer in merchant, fill in merchant APPID at present
remark        String      required     Remark Field
============ =========== ============= =====================================================================


:Example request parameters:

::

	app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=pvcuCqVIu6aKQotQ1Z5WRzevdO3s81UReMZWvc_K7YGF1gCKkae0sPhlHogIU0slUWTME4bHzbZCl15Qg-RlnECqkTxiOazZTEmPi9vNJlO4V5awPYA9fbBM6pTvQxE-Qwsg9M6IyX6VcnRxiaqLJxRbZwoF0g4vBeRdcmGCqNOp3V6eY4s3-DTXmVDtF0eicPM0ROuWEjCThxNbPqy3CW2ldBtnigpxZ2A5ajlLLln8o9pb04kKrxdC4hVMJlrv0J5Bonn0gNP_355-ElB0L4ttyH-x8Uc3jfe2w6n46bODUaXUXsJoNmDZBC7bEJQj1axwrudFE7YasEfM9OCGdzvzOVgUFi-aHqLfA9aTwgK7vw3QOX4ypfK669qGiqiiJMBfGw6_209SquIn535eMZh8rrGZIb1I7xIifNWiYNtRkeHvIF16_jLNTCMZO0wVmMID3j4eEtxkO65RMYHMu0FUwehw1bQB7nVYafvcLa4tZqUDM_YcyK4BVqDgqcBSdVCCnppEMy-OHXMhebhuI6U81UG9YJ5E1eePg1kr_IPvMj-DFAaUXEde53k4AZsGR0vPP1N0k5lj0-GrmlsLtlt2GhubpgnGw0SyRExwu4zzpaBhU0Im1uwUvKxTOb1abD2ELB0mbMsucH47gKe-2-ta8opEpfDutsaf7B-6d8M

:Response parameters:


========= ========== ============= ============================================================================
Param	    type       required       Description
data      String     Optional       The encrypted string and the decrypted format are defined as follows
========= ========== ============= ============================================================================


:After the response parameter data is decrypted:

========= ========== ============= ========================================================================
Param	    type       required       Description
code	    String     required	      Status code
msg       String     required       Response result description
data      String     Optional       For specific response data, the data structure is defined as follows
========= ========== ============= ========================================================================


:Data structure:


===================== ========== =========== =================================================
Param                 type       required     Description
receipt               String     required     Unique voucher for transfer
===================== ========== =========== =================================================



:Example response:

::

	{"data":"k4w5AijeFWF3AtYbgP1RYfej7ifW4R663pOt5bhQp8RIxFUVb6zKOy4snKukA_5T9DVwhjdhsHjSRpmxD5LwL2OtplwSUACRPnW39ANypjO5YeMJTpiY9_7jofZWYzAMB4gdkrAI3DAbvkjCFUKQIXfAGMl25sp05mdBZgfY1oEtveSyislYOwaLM3SfN_2bFvrKy7E2V0AkZhrYImKiCzmDZvE-i93cePVQ4ODiuusHgk1vH5QgvPv62Sh-xxQPb4TsWj2G_RBoo9dFlg4zbWOdb9z6SVzR86ouxKOX_RhE4vWsReVD4ukdsW8eO7SVCI74qc61hIS12X6u-Hv40g"}

:Example after response data decryption:


::

	{
	    "code":"0",
	    "data":[
	        {
	            "receipt":"abcdesd",
	        }
	    ],
	    "msg":"success"
	}





Transfer information is confirmed asynchronously
~~~~~~~~~~~~~~~~~~~~~~~~

:Description: Transfer information is confirmed asynchronously
:Interface address: /same-with-withdraw-check-sum
:Request method: POST
:Request parameters:


========= ========== ============= =============================================================================
Param	    type       required      Description
app_id	  String	   可选	          Merchant's unique identification
data      String	   可选	          The encrypted string and the decrypted format are defined as follows
========= ========== ============= =============================================================================

:Data structure after decryption of request parameter data:

============ =========== ============= ==============================================================================================================================
Param	         type         required      Description
time	         Long	        required	    Current timestamp
charset        String       required      Coding format, no special case, transfer parameter UTF-8
version        String       required      Interface version number, no special case, transfer parameter v2
request_id     String       required      Request unique identification, up to 64 bits
symbol	       String       required      currency
amount         String       required      Transfer quantity, including transfer fees
to             String       required      fill in merchant appid at present
check_sum      String       required      Random check code. The third party returns this field as it is. The platform considers it successful
remark         String       required      Remark Field
============ =========== ============= ==============================================================================================================================


:Example request parameters:

::

   app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=pvcuCqVIu6aKQotQ1Z5WRzevdO3s81UReMZWvc_K7YGF1gCKkae0sPhlHogIU0slUWTME4bHzbZCl15Qg-RlnECqkTxiOazZTEmPi9vNJlO4V5awPYA9fbBM6pTvQxE-Qwsg9M6IyX6VcnRxiaqLJxRbZwoF0g4vBeRdcmGCqNOp3V6eY4s3-DTXmVDtF0eicPM0ROuWEjCThxNbPqy3CW2ldBtnigpxZ2A5ajlLLln8o9pb04kKrxdC4hVMJlrv0J5Bonn0gNP_355-ElB0L4ttyH-x8Uc3jfe2w6n46bODUaXUXsJoNmDZBC7bEJQj1axwrudFE7YasEfM9OCGdzvzOVgUFi-aHqLfA9aTwgK7vw3QOX4ypfK669qGiqiiJMBfGw6_209SquIn535eMZh8rrGZIb1I7xIifNWiYNtRkeHvIF16_jLNTCMZO0wVmMID3j4eEtxkO65RMYHMu0FUwehw1bQB7nVYafvcLa4tZqUDM_YcyK4BVqDgqcBSdVCCnppEMy-OHXMhebhuI6U81UG9YJ5E1eePg1kr_IPvMj-DFAaUXEde53k4AZsGR0vPP1N0k5lj0-GrmlsLtlt2GhubpgnGw0SyRExwu4zzpaBhU0Im1uwUvKxTOb1abD2ELB0mbMsucH47gKe-2-ta8opEpfDutsaf7B-6d8M

:Response parameters:

========= ========== ============= ==================================================================================
Param	    type       required       Description
data      String     Optional       The encrypted string and the decrypted format are defined as follows
========= ========== ============= ==================================================================================


:After the response parameter data is decrypted:

========= ========== ============= =============================================================================
Param	    type       required       Description
code	    String     required	      Status code
msg       String     required       Response result description
data      String     Optional       For specific response data, the data structure is defined as follows
========= ========== ============= =============================================================================


:Data structure:

============ =========== ============= ==================================================================================================================
Param	       type         required       Description
time	       long	        required	     Current timestamp
check_sum    String       required       Random check code. The third party returns this field as it is. The platform considers it successful
============ =========== ============= ==================================================================================================================



:响应示例:

::

   {"data":"k4w5AijeFWF3AtYbgP1RYfej7ifW4R663pOt5bhQp8RIxFUVb6zKOy4snKukA_5T9DVwhjdhsHjSRpmxD5LwL2OtplwSUACRPnW39ANypjO5YeMJTpiY9_7jofZWYzAMB4gdkrAI3DAbvkjCFUKQIXfAGMl25sp05mdBZgfY1oEtveSyislYOwaLM3SfN_2bFvrKy7E2V0AkZhrYImKiCzmDZvE-i93cePVQ4ODiuusHgk1vH5QgvPv62Sh-xxQPb4TsWj2G_RBoo9dFlg4zbWOdb9z6SVzR86ouxKOX_RhE4vWsReVD4ukdsW8eO7SVCI74qc61hIS12X6u-Hv40g"}

:Example after response data decryption:


::

	{
    "code":"0",
    "data":[
        {
            "time":1551429063111,
            "check_sum":"123124",
        }
    ],
    "msg":"success"
	}




Batch query transfer records
~~~~~~~~~~~~~~~~~~~~~~~~

:Description: Batch query transfer records
:The interface address: /api/v2/account/transferList
:Request method: POST
:Request parameters:


========= ========== ============= ==============================================================================
Param	    Type       required      Description
app_id	  String	   Optional	     Merchant's unique identification
data      String	   Optional	     The encrypted string and the decrypted format are defined as follows
========= ========== ============= ==============================================================================

:Data structure after decryption of request parameter data:

========== =============== ================== ==================================================================================================
Param	        Type           required         Description
time	        long	         required	        Current timestamp
charset       String         required         Coding format, no special case, transfer parameter UTF-8
version       String         required         Interface version number, no special case, transfer parameter v2
ids           String         required         Request a unique identifier. Multiple identifiers are separated by English commas, up to 100
ids_type      String         required         request_id：request ID (default); receipt: transfer voucher
========== =============== ================== ==================================================================================================


:Example request parameters:

::

   app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=pvcuCqVIu6aKQotQ1Z5WRzevdO3s81UReMZWvc_K7YGF1gCKkae0sPhlHogIU0slUWTME4bHzbZCl15Qg-RlnECqkTxiOazZTEmPi9vNJlO4V5awPYA9fbBM6pTvQxE-Qwsg9M6IyX6VcnRxiaqLJxRbZwoF0g4vBeRdcmGCqNOp3V6eY4s3-DTXmVDtF0eicPM0ROuWEjCThxNbPqy3CW2ldBtnigpxZ2A5ajlLLln8o9pb04kKrxdC4hVMJlrv0J5Bonn0gNP_355-ElB0L4ttyH-x8Uc3jfe2w6n46bODUaXUXsJoNmDZBC7bEJQj1axwrudFE7YasEfM9OCGdzvzOVgUFi-aHqLfA9aTwgK7vw3QOX4ypfK669qGiqiiJMBfGw6_209SquIn535eMZh8rrGZIb1I7xIifNWiYNtRkeHvIF16_jLNTCMZO0wVmMID3j4eEtxkO65RMYHMu0FUwehw1bQB7nVYafvcLa4tZqUDM_YcyK4BVqDgqcBSdVCCnppEMy-OHXMhebhuI6U81UG9YJ5E1eePg1kr_IPvMj-DFAaUXEde53k4AZsGR0vPP1N0k5lj0-GrmlsLtlt2GhubpgnGw0SyRExwu4zzpaBhU0Im1uwUvKxTOb1abD2ELB0mbMsucH47gKe-2-ta8opEpfDutsaf7B-6d8M

:Response parameters:


========= ========== ============= ============================================================================================
Param	    Type       required       Description
data      String     Optional       The encrypted string and the decrypted format are defined as follows
========= ========== ============= ============================================================================================


:After the response parameter data is decrypted:

========= ========== ============= ==================================================================================
Param	    Type       required        Description
code	    String     required	       Status code
msg       String     required        Response result description
data      String     Optional        For specific response data, the data structure is defined as follows
========= ========== ============= ==================================================================================


:Data structure:


============ ========= =============== ============================================================================
Param	        Type      required         Description
time	        long	    required	       Current timestamp
charset       String    required         Coding format, no special case, transfer parameter UTF-8
version       String    required         Interface version number, no special case, transfer parameter v2
id            String    required         Request unique identification, up to 64 bits
symbol	      String    required         currency
amount        String    required         Transfer quantity, including transfer fees
from          String    required         Transfer out merchant, transfer out merchant APPID
to            String    required         Transfer in merchant, transfer in merchant APPID
created_at    Long      required         Creation time
request_id    String    required         Tripartite ID
receipt       String    required         Transfer voucher
remark        String    required         Up to 32 characters
============ ========= =============== ============================================================================



:Example response:

::

   {"data":"k4w5AijeFWF3AtYbgP1RYfej7ifW4R663pOt5bhQp8RIxFUVb6zKOy4snKukA_5T9DVwhjdhsHjSRpmxD5LwL2OtplwSUACRPnW39ANypjO5YeMJTpiY9_7jofZWYzAMB4gdkrAI3DAbvkjCFUKQIXfAGMl25sp05mdBZgfY1oEtveSyislYOwaLM3SfN_2bFvrKy7E2V0AkZhrYImKiCzmDZvE-i93cePVQ4ODiuusHgk1vH5QgvPv62Sh-xxQPb4TsWj2G_RBoo9dFlg4zbWOdb9z6SVzR86ouxKOX_RhE4vWsReVD4ukdsW8eO7SVCI74qc61hIS12X6u-Hv40g"}

:Example after response data decryption:


::

	{
    "code":"0",
    "data":[
        {
            "id":"123",
            "symbol":"ETH",
            "amount":"0.002",
            "from":"0xc0ff095a9f1608f6873e74b84671640364107dc4",
            "to":"0xc0ff095a9f1608f6873e74b84671640364107dc5",
            "created_at":1551429063000,
            "request_id":"123123",
            "receipt":"4444444",
            "remark":"remark"
        }
        {
            "id":"124",
            "symbol":"ETH",
            "amount":"0.002",
            "from":"0xc0ff095a9f1608f6873e74b84671640364107dc4",
            "to":"0xc0ff095a9f1608f6873e74b84671640364107dc5",
            "created_at":1551429063111,
            "request_id":"123124",
            "receipt":"4444445",
            "remark":"remark"
        }
    ],
    "msg":"success"
	}





Synchronous transfer record
~~~~~~~~~~~~~~~~~~~~~~~~

:Description: Synchronize all transfer records (paging)
:The interface address: /api/v2/account/syncTransferList
:Request method: POST
:Request parameters:


========= ========== ============= =================================================================================
Param	    type       required       Description
app_id	  String	   Optional	      Merchant's unique identification
data      String	   Optional	      The encrypted string and the decrypted format are defined as follows
========= ========== ============= =================================================================================

:Data structure after decryption of request parameter data:
========= ========== ============= ====================================================================================
Param	    type       required       Description
time	    long	     required	      Current timestamp
charset   String     required       Coding format, no special case, transfer parameter UTF-8
version   String     required       Interface version number, no special case, transfer parameter v2
max_id    String     required       Return the data of 100 transfer records greater than ID
========= ========== ============= ====================================================================================


:Example request parameters:

::

   app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=pvcuCqVIu6aKQotQ1Z5WRzevdO3s81UReMZWvc_K7YGF1gCKkae0sPhlHogIU0slUWTME4bHzbZCl15Qg-RlnECqkTxiOazZTEmPi9vNJlO4V5awPYA9fbBM6pTvQxE-Qwsg9M6IyX6VcnRxiaqLJxRbZwoF0g4vBeRdcmGCqNOp3V6eY4s3-DTXmVDtF0eicPM0ROuWEjCThxNbPqy3CW2ldBtnigpxZ2A5ajlLLln8o9pb04kKrxdC4hVMJlrv0J5Bonn0gNP_355-ElB0L4ttyH-x8Uc3jfe2w6n46bODUaXUXsJoNmDZBC7bEJQj1axwrudFE7YasEfM9OCGdzvzOVgUFi-aHqLfA9aTwgK7vw3QOX4ypfK669qGiqiiJMBfGw6_209SquIn535eMZh8rrGZIb1I7xIifNWiYNtRkeHvIF16_jLNTCMZO0wVmMID3j4eEtxkO65RMYHMu0FUwehw1bQB7nVYafvcLa4tZqUDM_YcyK4BVqDgqcBSdVCCnppEMy-OHXMhebhuI6U81UG9YJ5E1eePg1kr_IPvMj-DFAaUXEde53k4AZsGR0vPP1N0k5lj0-GrmlsLtlt2GhubpgnGw0SyRExwu4zzpaBhU0Im1uwUvKxTOb1abD2ELB0mbMsucH47gKe-2-ta8opEpfDutsaf7B-6d8M

:Response parameters:


========= ========== ============= ========================================================================================
Param	    type       required       Description
data      String     Optional       The encrypted string and the decrypted format are defined as follows
========= ========== ============= ========================================================================================


:After the response parameter data is decrypted:

========= ========== ============= ===============================================================================
Param	    type       required        Description
code	    String     required	       Status code
msg       String     required        Response result description
data      String     Optional        For specific response data, the data structure is defined as follows
========= ========== ============= ===============================================================================


:Data structure:
============ =========== ============= ============================================================================
Param	         type         required       Description
time	         long	        required	     Current timestamp
charset        String       required       Encoding format, no special case, pass utf-8
version        String       required       Interface version number, no special case, pass v2
id             String       required       Unique request identifier, up to 64 bits
symbol	       String       required       currency
amount         String       required       Number of transfers, including transfer fees
from           String       required       The transferring merchant, the APPID of the transferring merchant
to             String       required       The incoming merchant and the incoming merchant's APPID
created_at     Long         required       Creation time
request_id     String       required       Tripartite ID
receipt        String       required       Transfer voucher
remark         String       required       Maximum 32 characters
============ =========== ============= ============================================================================



:Example response:

::

   {"data":"k4w5AijeFWF3AtYbgP1RYfej7ifW4R663pOt5bhQp8RIxFUVb6zKOy4snKukA_5T9DVwhjdhsHjSRpmxD5LwL2OtplwSUACRPnW39ANypjO5YeMJTpiY9_7jofZWYzAMB4gdkrAI3DAbvkjCFUKQIXfAGMl25sp05mdBZgfY1oEtveSyislYOwaLM3SfN_2bFvrKy7E2V0AkZhrYImKiCzmDZvE-i93cePVQ4ODiuusHgk1vH5QgvPv62Sh-xxQPb4TsWj2G_RBoo9dFlg4zbWOdb9z6SVzR86ouxKOX_RhE4vWsReVD4ukdsW8eO7SVCI74qc61hIS12X6u-Hv40g"}

:Example after response data decryption:


::

	{
    "code":"0",
    "data":[
        {
            "id":"123",
            "symbol":"ETH",
            "amount":"0.002",
            "from":"0xc0ff095a9f1608f6873e74b84671640364107dc4",
            "to":"0xc0ff095a9f1608f6873e74b84671640364107dc5",
            "created_at":1551429063000,
            "request_id":"123123",
            "receipt":"4444444",
            "remark":"remark"
        }
        {
            "id":"124",
            "symbol":"ETH",
            "amount":"0.002",
            "from":"0xc0ff095a9f1608f6873e74b84671640364107dc4",
            "to":"0xc0ff095a9f1608f6873e74b84671640364107dc5",
            "created_at":1551429063111,
            "request_id":"123124",
            "receipt":"4444445",
            "remark":"remark"
        }
    ],
    "msg":"success"
	}
