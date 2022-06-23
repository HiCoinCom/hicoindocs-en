Account balance
==============


Query user information
-------------------

:Description: Query user information
:Interface address: /api/v2/user/info
:Request method:  GET
:Request parameters:

========= ========== ============= ===================================================
Param	    type       required      Description
app_id	  String	   optional	     merchant unique identifier
data      String	   optional	     decrypted format is defined as follows
========= ========== ============= ===================================================

:Data structure after decryption of request parameter data:

========= ======= ========== =================================================================================
Param     type    required   Description
time      long    required   current timestamp
charset   String  required   encoding format, no special case, pass parameter UTF-8
version   String  required   interface version number, no special case, pass parameter v2
country	  String	optional	 Country number, Mobile is not empty, this field is required. Such as: 86
mobile	  String	optional	 Phone Number, Phone and Email must be made sure that one of them is not empty
email     string	optional	 Email, Phone, and Email must be made sure that one of them is not empty
========= ======= ========== =================================================================================


:Example request parameters:

::

	app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=GCJBk77n7epyOexdGZ20qvukd321TpJ62lIAtlCinW6TzHx8SIbm6evXGulO87UgLTzIWCtgupgeLJKDdZmC7msuPNBGK--Ec27WZXjuhI0gNWXcOVk5RW_VRVcyfJ1Ml-DMW8XVxZRgA2U1bt9BztiyfryzMGj8_jl1IXd5sOQfPYXulCdm70WyTJpjsDkuMSov6QUmOn-C_-HUoZ7s715EMeZ60D09uUsF0i6mKLhFZTEQZPGPeJITYSJNddAw7nvqvX2KzNc6YUeCQhEmU1Dfxp65W4e3SVOgpd_2Q-dLN1MpOlkUKwbmbpb-gEh_s68yl7ox6WSgKfCK4i_uvA



:Response parameters:

========= ========== ============= ===================================================
Param	    type       required      Description
data      String     optional      decrypted format is defined as follows
========= ========== ============= ===================================================


:After the response parameter data is decrypted:

========= ========== ============= ===================================================
Param	    type       required      Description
code	    String     required	     status code
msg       String     required      the description of the response result
data      String     optional      the specific response data
========= ========== ============= ===================================================

:data structure:

========= ========== ============= =======================================================
Param     type       required      Description
uid       int        required      the unique identity of the user in the wallet service
nickname  String     required      the nickname of the user
========= ========== ============= =======================================================



:Example response:

::

	{"data":"LK4D5mrtvTubDxCQM4lqyN2h8TTIkEBL_06FrrrzLrImyMO4Yuac-wdbk5VnGVfCKB5EFaUb162xXUJdTHhpA5CGBCAQKl64h_Dt10C-H8KIoap9dZI90qE4f-mAMAyjF1QzKXJ-f-R_3J3bRGqfHFBRXebh08R8MdRDssniopVOhsFUs4gBxUensKas3_ta15eFIqXPjIgJWfYQCD2DUi1gaKgmN-5Q_tgt-qXp5Y2uh3yfM4g4k71Ahyel3G8S_AktbWl2G9wU3cri3ZVQEo0faIpkX_CKsk9V1YoY5yRopvJbxNtkG9lBFxKnureAQo0KP3f1tsIMOzgcyEXPnA"}

:Example after response data decryption:

::

	{"code":"0","data":{"uid":3529218,"nickname":""},"msg":"success"}






Obtain a list of supported currencies
-------------------

:Description: Get a list of the currencies of the merchant
:Interface address: /api/v2/user/getCoinList
:Request method: GET
:Request parameters:

========= ========== ============= =========================================================
Param	    type       required      Description
app_id	  String	   optional	     merchant unique identifier
data      String	   optional	     encrypted String, decrypted format is defined as follows
========= ========== ============= =========================================================

:Data structure after decryption of request parameter data:

========= ======= ========== ===============================================================
Param     type    required   Description
time      long    required	 current timestamp
charset   String  required   encoding format, no special case, pass parameter UTF-8
version   String  required   interface version number, no special case, pass parameter v2
========= ======= ========== ===============================================================


:Example request parameters:

::

  app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=GCJBk77n7epyOexdGZ20qvukd321TpJ62lIAtlCinW6TzHx8SIbm6evXGulO87UgLTzIWCtgupgeLJKDdZmC7msuPNBGK--Ec27WZXjuhI0gNWXcOVk5RW_VRVcyfJ1Ml-DMW8XVxZRgA2U1bt9BztiyfryzMGj8_jl1IXd5sOQfPYXulCdm70WyTJpjsDkuMSov6QUmOn-C_-HUoZ7s715EMeZ60D09uUsF0i6mKLhFZTEQZPGPeJITYSJNddAw7nvqvX2KzNc6YUeCQhEmU1Dfxp65W4e3SVOgpd_2Q-dLN1MpOlkUKwbmbpb-gEh_s68yl7ox6WSgKfCK4i_uvA


:Response parameters:

========= ========== ============= ===========================================================
Param	    type       required      Description
data      String     optional      encrypted String, decrypted format is defined as follows
========= ========== ============= ===========================================================


:After the response parameter data is decrypted:

========= ========== ============= ===================================================
Param	    type       required      Description
code	    String     required	     status code
msg       String     required      the description of the response result
data      String     optional      the specific response data
========= ========== ============= ===================================================

:Data structure:

========== ======= =========== ====================================================
Param      type    required    Description
symbol     String  required    currency(Be sure to use the value returned by this field when calling the interface to withdraw coins, and any query interface)
icon       String  required    currency icon
real_symbol String  required   Cryptocurrency on-chain names
========== ======= =========== ====================================================



:Example response:

::

  {"data":"LK4D5mrtvTubDxCQM4lqyN2h8TTIkEBL_06FrrrzLrImyMO4Yuac-wdbk5VnGVfCKB5EFaUb162xXUJdTHhpA5CGBCAQKl64h_Dt10C-H8KIoap9dZI90qE4f-mAMAyjF1QzKXJ-f-R_3J3bRGqfHFBRXebh08R8MdRDssniopVOhsFUs4gBxUensKas3_ta15eFIqXPjIgJWfYQCD2DUi1gaKgmN-5Q_tgt-qXp5Y2uh3yfM4g4k71Ahyel3G8S_AktbWl2G9wU3cri3ZVQEo0faIpkX_CKsk9V1YoY5yRopvJbxNtkG9lBFxKnureAQo0KP3f1tsIMOzgcyEXPnA"}

:Example after response data decryption:

::

  {
    "code":"0",
    "data":[
        {
            "symbol":"BTC",
            "icon":"http://chainup-oss.oss-cn-beijing.aliyuncs.com/saas/1565681771193.png",
            "real_symbol":"BTC",
            "decimals":"8",
            "name":"Bitcoin",
            "base_symbol":"BTC",
            "contract_address":"",
            "deposit_confirmation":"2",
            "explorer":"https://btc.com/",
            "address_regex":"^(1|3)[a-zA-Z0-9]{24,36}$",
            "address_tag_regex":"",
            "support_memo":"0",
            "support_token":"0"
	    
  }






Obtain the account information for the specified user
----------------------

:Description: Search the user's account according to the currency and user ID. In addition, if the merchant starts automatic collection, the user account will be transferred to the merchant's collection account
:The interface address: /api/v2/account/getByUidAndSymbol
:Request method: GET
:Request parameters:

========= ========== ============= =======================================================
Param	    type       required      Description
app_id	  String	   optional	     merchant unique identifier
data      String	   optional	     encrypted String decrypted format defined as follows:
========= ========== ============= =======================================================

:Data structure after decryption of request parameter data:

========= ======= ========== =============================================================
Param     type    required   Description
time      long    required   current timestamp
charset   String  required   encoding format, no special case, pass parameter UTF-8
vesion    String  required   interface version number, no special case, pass parameter v2
uid       String  required	 user ID
symbol    String  required	 currency
========= ======= ========== =============================================================



:Example request parameters:

::

	app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=gxakMvhB3jCRn05W6GnZHtLyvnW11n-OgF6KinF-0azrubfLG45H1TPd76cGTq7DccyVlNHGlXR7aNpa9bRsDmPHtcILn0HGno2glIOItQTGLuiS_DOQaNKBhtf5VD-CZyyC3hKPxyPUuTdEV3D57oUy2BUIykwUFpO_rhCyZKMVmUHuzYL2jIyAATb6-cbfrJuzdB8IlsyvkTOxbltI45Ie3V7JI31pMwsyN5Q8qW1kGSxjcaQOeT43-3Em8y9bl4KRHkGC5UJdlhnHJogPK3kPqATHS6zJsziBiKRpjBnrOtV4HndzoHMk4SQuijvy0fdQ0KCkOAFJL7lAtp8p4Q


:Response parameters:

========= ========== ============= =======================================================
Param	    type       required      Description
data      String     optional      encrypted String decrypted format defined as follows:
========= ========== ============= =======================================================


:After the response parameter data is decrypted:

========= ========== ============= ======================================================================
Param	    type       required      Description
code	    String     required	     status code
msg       String     required      the description of the response result
data      String     optional      the specific response data the data structure is defined as follows:
========= ========== ============= ======================================================================

:Data structure:

================= ========== ============= ===================================================
Param	            type       required      Description
normal_balance    String     required      normal account balance
lock_balance      String     required      freeze account balance
deposit_address   String     required      deposit_address
================= ========== ============= ===================================================



:Example response:

::

	{"data":"LK4D5mrtvTubDxCQM4lqyN2h8TTIkEBL_06FrrrzLrImyMO4Yuac-wdbk5VnGVfCKB5EFaUb162xXUJdTHhpA5CGBCAQKl64h_Dt10C-H8KIoap9dZI90qE4f-mAMAyjF1QzKXJ-f-R_3J3bRGqfHFBRXebh08R8MdRDssniopVOhsFUs4gBxUensKas3_ta15eFIqXPjIgJWfYQCD2DUi1gaKgmN-5Q_tgt-qXp5Y2uh3yfM4g4k71Ahyel3G8S_AktbWl2G9wU3cri3ZVQEo0faIpkX_CKsk9V1YoY5yRopvJbxNtkG9lBFxKnureAQo0KP3f1tsIMOzgcyEXPnA"}

:Example after response data decryption:

::

  {"code":"0","data":{"normal_balance":"2.99400066","deposit_address":"0x6956f9af53b22117f2fc94dfe7c74ff3893b2acd","lock_balance":"0"},"msg":"success"}






Obtain the balance of merchant collection account
---------------------

:Description: After opening the automatic collection of merchant funds, the merchant can obtain the balance of merchant collection account through this interface
:The interface address: /api/v2/account/getCompanyBySymbol
:Request method: GET
:Request parameters:

========= ========== ============= =======================================================
Param	    type       required      Description
app_id	  String	   optional	     merchant unique identifier
data      String	   optional	     encrypted String decrypted format defined as follows:
========= ========== ============= =======================================================

:Data structure after decryption of request parameter data:

========= ======= ========== ==============================================================
Param     type    required   Description
time      long    required   current timestamp
charset   String  required   encoding format, no special case, pass parameter UTF-8
vesion    String  required   interface version number, no special case, pass parameter v2
symbol    String  required	 currency
========= ======= ========== ==============================================================



:Example request parameters:

::

	app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=YepWL0rl-SK3qhhHrH-Nk-0ohFqkhV33cLXRHHmIIDJ1GJbfy5aUHWxrG342gxkPvdQF-Hnq3ajez2eqrJIisNCXiUw7-f2TgXUdSlShGF-6I7QeSinclCbKj-sqsRpRS9lFFTGWz-GUuUJiWkgK6mCsEH3xMKM-14nHKU6R1K7lbsPMn61E4P8lxtkWs9uwB97hHADzSJswXF-jTCqY2xYZDILXQTm6wwMFVL3ynIV9YWosprAVOrkQ9hawxRl9vmJDvF85JI8qNaNMcmwlLNzBPLdeQJHjRTEkj2BtiNk3gU8IYAWifwVv0alFb8zrVIJbEm4S_GfybB2oOzNmOQ

:Response parameters:

========= ========== ============= =======================================================
Param	    type       required      Description
data      String     optional      encrypted String decrypted format defined as follows
========= ========== ============= =======================================================


:After the response parameter data is decrypted:

========= ========== ============= ==========================================================================
Param	    type       required      Description
code	    String     required	     status code
msg       String     required      the description of the response result
data      String     optional      the specific response data the data structure is defined as follows:
========= ========== ============= ==========================================================================

:Data structure:

================= ========== ============= ===================================================
Param	            type       required      Description
symbol            String     required      currency name
balance           String     required      collection account balance
================= ========== ============= ===================================================



:Data structure:

::

	{"data":"jwtkGrhh2EVJS8xe93MpUYd-SQ-TyK0Bx5sXjE4hygFNg4wmctiahtIYXRpR2j8yDaEF5YzVstnUKbOH2p44FSMjXMQU4qFrhD00WOfW7v4LNALyiQXRb_5sakR0Zf573lGfLRTPlzLtTho3gqu3hMwuAv5e3r2dpb6_jxh1Z9BjkzSsNRX_bjLcHLUOPhMvo6rTUKSa9LQ6QnT8RX0eqzOZPlnCw3TeX_zcWWjxp6fcpKcdODxoI86gHwWRpSd-2qbEbFcaT12CJd9nPXA0KnLPNNHWz8sxQGiAg7Jg_-cN_yBHL9cS15zecTemYGqpOXRkojM1JwLsjM-7txf_dw"}


:Example response:

::

	{"code":"0","data":{"symbol":"ETH","balance":"64.97599802"},"msg":"success"}
