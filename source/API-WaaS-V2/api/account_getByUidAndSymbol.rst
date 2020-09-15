
2.5 Get User Account Information by Symbol and Uid
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:URI: /api/v2/account/getByUidAndSymbol
:Method: GET
:Request Parameters:
=========== =========== =========== =====================================================================================================================
Params	    Type        Required 	  Description
app_id      String      Y           app id
data        String      Y           The request parameters after encryption and the data structure after decryption are defined as follows
=========== =========== =========== =====================================================================================================================

:Data Structure After Request Parameter Data Decryption:
=========== =========== =========== ============================================
Params	    Type         Required   Description
time        long         Y          timestamp
charset     String       Y          Encoding format, default parameter utf-8
vesion      String       Y          api vesion, default parameter v2
uid         String       Y          user id
symbol      String       Y          symbol
=========== =========== =========== ============================================

:Example of Request Parameter:

::

	app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=gxakMvhB3jCRn05W6GnZHtLyvnW11n-OgF6KinF-0azrubfLG45H1TPd76cGTq7DccyVlNHGlXR7aNpa9bRsDmPHtcILn0HGno2glIOItQTGLuiS_DOQaNKBhtf5VD-CZyyC3hKPxyPUuTdEV3D57oUy2BUIykwUFpO_rhCyZKMVmUHuzYL2jIyAATb6-cbfrJuzdB8IlsyvkTOxbltI45Ie3V7JI31pMwsyN5Q8qW1kGSxjcaQOeT43-3Em8y9bl4KRHkGC5UJdlhnHJogPK3kPqATHS6zJsziBiKRpjBnrOtV4HndzoHMk4SQuijvy0fdQ0KCkOAFJL7lAtp8p4Q


:Response Parameters:

=========== =========== =========== =====================================================================================================================
Params	    Type        Required    Description
data        String      Y           The request parameters after encryption and the data structure after decryption are defined as follows
=========== =========== =========== =====================================================================================================================


:The Data Structure after Decryption:

=========== =========== =========== =========================================================
Params	    Type        Required    Description
code        String      Y	          Error code
msg         String      Y           Message
data        String      Y           Response data, the data structure is defined as follows
=========== =========== =========== =========================================================

:Data Structure:

================= =========== =========== =========================================================
Params            Type        Required    Description
normal_balance    String      Y           Normal account balance
lock_balance      String      Y           Locked account balance
deposit_address   String      Y           Deposit address
================= =========== =========== =========================================================



:Example of Response Data:

::

	{"data":"LK4D5mrtvTubDxCQM4lqyN2h8TTIkEBL_06FrrrzLrImyMO4Yuac-wdbk5VnGVfCKB5EFaUb162xXUJdTHhpA5CGBCAQKl64h_Dt10C-H8KIoap9dZI90qE4f-mAMAyjF1QzKXJ-f-R_3J3bRGqfHFBRXebh08R8MdRDssniopVOhsFUs4gBxUensKas3_ta15eFIqXPjIgJWfYQCD2DUi1gaKgmN-5Q_tgt-qXp5Y2uh3yfM4g4k71Ahyel3G8S_AktbWl2G9wU3cri3ZVQEo0faIpkX_CKsk9V1YoY5yRopvJbxNtkG9lBFxKnureAQo0KP3f1tsIMOzgcyEXPnA"}

:Example of Response Data after Decryption:

::

	{"code":"0","data":{"normal_balance":"2.99400066","deposit_address":"0x6956f9af53b22117f2fc94dfe7c74ff3893b2acd","lock_balance":"0"},"msg":"success"}
