
2.7 Get User's Deposit Address
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:URI: /api/v2/account/getDepositAddress
:Method: POST
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



:Request of Parameter Example:

::

	app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=GCJBk77n7epyOexdGZ20qvukd321TpJ62lIAtlCinW6TzHx8SIbm6evXGulO87UgLTzIWCtgupgeLJKDdZmC7msuPNBGK--Ec27WZXjuhI0gNWXcOVk5RW_VRVcyfJ1Ml-DMW8XVxZRgA2U1bt9BztiyfryzMGj8_jl1IXd5sOQfPYXulCdm70WyTJpjsDkuMSov6QUmOn-C_-HUoZ7s715EMeZ60D09uUsF0i6mKLhFZTEQZPGPeJITYSJNddAw7nvqvX2KzNc6YUeCQhEmU1Dfxp65W4e3SVOgpd_2Q-dLN1MpOlkUKwbmbpb-gEh_s68yl7ox6WSgKfCK4i_uvA

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
address           String      Y           deposit address
================= =========== =========== =========================================================



:Example of Response Data:

::

	{"data":"C6vPlXILSVMFOY4yzXMQ3lNmNRLbnfCIlIwgRXo3UXH152rKma-9vq8dEomWNOOhCxhsW-cV7bh1SpYQg2ehK5QbcIbrCdIyuD87QPyAUnXn5UgEWcYQU_6stj8yazgv5o6QfAZbe5AUDs4rjU55NziDI0Ml9bbpkk1u9PhH8L5s2uoYjjDkjTqk_KQx9Mjt42VvDkfaWUuAsaF3V0uqaCVEvnx0yQXS_lr4zRsNptspnHGJwXnvhBMRN3EEkpG_IdlkndK3Lujwe96vlqPQawLE1nDE7VsPwJq-4S-2GHOtUPMzdBXAGIHnDFeMT03ExXWBMWutng89itdFR6zRUg"}

:Example of Response Data after Decryption:

::

	{"code":"0","data":{"uid":"3529218","address":"0x6956f9af53b22117f2fc94dfe7c74ff3893b2acd"},"msg":"success"}
