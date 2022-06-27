Get the address
==================


User Mobile Registration
~~~~~~~~~~~~~~~~~~~~~~~~

:Description: Register to become a wallet user
:Interface address: /api/v2/user/createUser
:Request method: POST
:Request parameters:

========= ========== ============= ====================================================================
Param	  type       required      Description
app_id	  String     optional	   merchant unique identifier
data      String     optional	   encrypted String,  decrypted format is defined as follows
========= ========== ============= ====================================================================

:Data structure after decryption of request parameter data:

========= ========== ============= ================================================================
Param     type       required      Description
time      long       required	   current timestamp
charset   String     required      encoding format, no special case, pass parameter UTF-8
version   String     required      interface version number, no special case, pass parameter v2
country	  String     required      country number, e.g. 86 for China
mobile	  String     required      mobile number
========= ========== ============= ================================================================



:Example request parameters:

::

	app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=GCJBk77n7epyOexdGZ20qvukd321TpJ62lIAtlCinW6TzHx8SIbm6evXGulO87UgLTzIWCtgupgeLJKDdZmC7msuPNBGK--Ec27WZXjuhI0gNWXcOVk5RW_VRVcyfJ1Ml-DMW8XVxZRgA2U1bt9BztiyfryzMGj8_jl1IXd5sOQfPYXulCdm70WyTJpjsDkuMSov6QUmOn-C_-HUoZ7s715EMeZ60D09uUsF0i6mKLhFZTEQZPGPeJITYSJNddAw7nvqvX2KzNc6YUeCQhEmU1Dfxp65W4e3SVOgpd_2Q-dLN1MpOlkUKwbmbpb-gEh_s68yl7ox6WSgKfCK4i_uvA


:Response parameters:

========= ========== ============= ===============================================================
Param	  type       required       Description
data      String     optional       encrypted String decrypted format is defined as follows：
========= ========== ============= ===============================================================


:After the response parameter data is decrypted:

========= ========== ============= ============================================================================
Param	  type       required      Description
code	  String     required	   status code
msg       String     required      description of the response result
data      String     optional      the specific response data, the data structure is defined as follows
========= ========== ============= ============================================================================

:Data structure:

========= ========== ============= ===================================================================
Param	  type       required      Description
uid       int        required      the unique identity of the user in the wallet service
========= ========== ============= ===================================================================



:Example response:

::

	{"data":"LK4D5mrtvTubDxCQM4lqyN2h8TTIkEBL_06FrrrzLrImyMO4Yuac-wdbk5VnGVfCKB5EFaUb162xXUJdTHhpA5CGBCAQKl64h_Dt10C-H8KIoap9dZI90qE4f-mAMAyjF1QzKXJ-f-R_3J3bRGqfHFBRXebh08R8MdRDssniopVOhsFUs4gBxUensKas3_ta15eFIqXPjIgJWfYQCD2DUi1gaKgmN-5Q_tgt-qXp5Y2uh3yfM4g4k71Ahyel3G8S_AktbWl2G9wU3cri3ZVQEo0faIpkX_CKsk9V1YoY5yRopvJbxNtkG9lBFxKnureAQo0KP3f1tsIMOzgcyEXPnA"}

:Example after response data decryption:

::

	{"code":"0","data":{"uid":3529218},"msg":"success"}






User email registration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:Description: egister to become a wallet user. Just meet the email format (e.g. 123@111.com)
:Interface address: /api/v2/user/registerEmail
:Request method: POST
:Request parameters:

========= ========== ============= ===============================================================
Param	  type       required      Description
app_id	  String     optional	   merchant unique identifier
data      String     optional	   encrypted String decrypted format is defined as follows：
========= ========== ============= ===============================================================


:Data structure after decryption of request parameter data:

========= ========== ============= =================================================================================
Param	  type       required      Description
time	  long	     required	   current timestamp
charset   String     required      encoding format, no special case, pass parameter UTF-8
version   String     required      interface version number, no special case, pass parameter v2
email	  String     required	   Email or Virtual Accounts, to ensure their uniqueness, up to 100 characters
========= ========== ============= =================================================================================



:Example request parameters:

::

	app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=GCJBk77n7epyOexdGZ20qvukd321TpJ62lIAtlCinW6TzHx8SIbm6evXGulO87UgLTzIWCtgupgeLJKDdZmC7msuPNBGK--Ec27WZXjuhI0gNWXcOVk5RW_VRVcyfJ1Ml-DMW8XVxZRgA2U1bt9BztiyfryzMGj8_jl1IXd5sOQfPYXulCdm70WyTJpjsDkuMSov6QUmOn-C_-HUoZ7s715EMeZ60D09uUsF0i6mKLhFZTEQZPGPeJITYSJNddAw7nvqvX2KzNc6YUeCQhEmU1Dfxp65W4e3SVOgpd_2Q-dLN1MpOlkUKwbmbpb-gEh_s68yl7ox6WSgKfCK4i_uvA


:Response parameters:

========= ========== ============= ============================================================
Param	  type       required       Description
data      String     optional       encrypted String, decrypted format is defined as follows：
========= ========== ============= ============================================================


:After the response parameter data is decrypted:

========= ========== ============= ===================================================================================
Param	  type       required      Description
code	  String     required	   status code
msg       String     required      the description of the response result
data      String     optional      the specific response data  the data structure is defined as follows：
========= ========== ============= ===================================================================================

:Data structure:

========= ========== ============= =============================================================
Param     type       required       Description
uid       int        required       the unique identity of the user in the wallet service
========= ========== ============= =============================================================



:Example response:

::

	{"data":"LK4D5mrtvTubDxCQM4lqyN2h8TTIkEBL_06FrrrzLrImyMO4Yuac-wdbk5VnGVfCKB5EFaUb162xXUJdTHhpA5CGBCAQKl64h_Dt10C-H8KIoap9dZI90qE4f-mAMAyjF1QzKXJ-f-R_3J3bRGqfHFBRXebh08R8MdRDssniopVOhsFUs4gBxUensKas3_ta15eFIqXPjIgJWfYQCD2DUi1gaKgmN-5Q_tgt-qXp5Y2uh3yfM4g4k71Ahyel3G8S_AktbWl2G9wU3cri3ZVQEo0faIpkX_CKsk9V1YoY5yRopvJbxNtkG9lBFxKnureAQo0KP3f1tsIMOzgcyEXPnA"}

:Example after response data decryption:

::

	{"code":"0","data":{"uid":3529218},"msg":"success"}






Obtain the address of the user specified currency
~~~~~~~~~~~~~~~~~~~~~~~~~~~

:Description: To obtain the user specified currency account address. If there is no address, the user is assigned an address, and the account should not be generated. The account is still generated on demand.
:The interface address: /api/v2/account/getDepositAddress
:Request method: POST
:Request parameters:


========= ========== ============= =============================================================
Param	  type       required      Description
app_id	  String     optional	   merchant unique identifier
data      String     optional	   encrypted String decrypted format defined as follows:
========= ========== ============= =============================================================

:Data structure after decryption of request parameter data:

========= ======= ========== =====================================================================
Param     type    required   Description
time      long    required   current timestamp
charset   String  required   encoding format, no special case, pass parameter UTF-8
vesion    String  required   interface version number, no special case, pass parameter v2
uid       String  required   user ID
symbol    String  required   currency
========= ======= ========== =====================================================================


:Example request parameters:

::

	app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=GCJBk77n7epyOexdGZ20qvukd321TpJ62lIAtlCinW6TzHx8SIbm6evXGulO87UgLTzIWCtgupgeLJKDdZmC7msuPNBGK--Ec27WZXjuhI0gNWXcOVk5RW_VRVcyfJ1Ml-DMW8XVxZRgA2U1bt9BztiyfryzMGj8_jl1IXd5sOQfPYXulCdm70WyTJpjsDkuMSov6QUmOn-C_-HUoZ7s715EMeZ60D09uUsF0i6mKLhFZTEQZPGPeJITYSJNddAw7nvqvX2KzNc6YUeCQhEmU1Dfxp65W4e3SVOgpd_2Q-dLN1MpOlkUKwbmbpb-gEh_s68yl7ox6WSgKfCK4i_uvA


:Response parameters:

========= ========== ============= ======================================================================
Param	  type       required      Description
data      String     optional      encrypted String decrypted format is defined as follows:
========= ========== ============= ======================================================================


:After the response parameter data is decrypted:

========= ========== ============= ===========================================================================
Param	  type       required      Description
code	  String     required	   status code
msg       String     required      the description of the response result
data      String     optional      the specific response data  the data structure is defined as follows:
========= ========== ============= ===========================================================================

:Data structure:

========= ========= ============= ===================================================
Param     type      required      Description
uid       int       required      the unique identity of the user in the wallet service
address   String    required      the currency account address
========= ========= ============= ===================================================



:Example response:

::

	{"data":"C6vPlXILSVMFOY4yzXMQ3lNmNRLbnfCIlIwgRXo3UXH152rKma-9vq8dEomWNOOhCxhsW-cV7bh1SpYQg2ehK5QbcIbrCdIyuD87QPyAUnXn5UgEWcYQU_6stj8yazgv5o6QfAZbe5AUDs4rjU55NziDI0Ml9bbpkk1u9PhH8L5s2uoYjjDkjTqk_KQx9Mjt42VvDkfaWUuAsaF3V0uqaCVEvnx0yQXS_lr4zRsNptspnHGJwXnvhBMRN3EEkpG_IdlkndK3Lujwe96vlqPQawLE1nDE7VsPwJq-4S-2GHOtUPMzdBXAGIHnDFeMT03ExXWBMWutng89itdFR6zRUg"}

:Example after response data decryption:

::

	{"code":"0","data":{"uid":"3529218","address":"0x6956f9af53b22117f2fc94dfe7c74ff3893b2acd"},"msg":"success"}
