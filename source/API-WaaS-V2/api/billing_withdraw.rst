
2.8 Withdrawal Interface
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:Note: If to_address is an internal address, the withdrawal interface functions the same as the internal transfer interface.
:URI: /api/v2/billing/withdraw
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
request_id  String       N          unique ID for each HTTP request
from_uid    String       N          from user id
to_address  String       N          withdrawal address
amount      String       N          transfer amount
symbol      String       N          symbol
=========== =========== =========== ============================================

:Example of Request Parameter:

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

============== ======= =========== =================================================
Params         Type    Required    Description
status         string  Y           explained as follows
withdraw_type  int     Y           1: withdraw, 2:Internal Transfer
============== ======= =========== =================================================

**Note:**

withdraw_type=1, status: 0 Unreviewed, 1 Reviewed，2 Review Rejected，3 Processing，4 failure, 5 complete;
withdraw_type=2, status: 0 success, 1 failure


:Example of Response Data:

::

	{"data":"k4w5AijeFWF3AtYbgP1RYfej7ifW4R663pOt5bhQp8RIxFUVb6zKOy4snKukA_5T9DVwhjdhsHjSRpmxD5LwL2OtplwSUACRPnW39ANypjO5YeMJTpiY9_7jofZWYzAMB4gdkrAI3DAbvkjCFUKQIXfAGMl25sp05mdBZgfY1oEtveSyislYOwaLM3SfN_2bFvrKy7E2V0AkZhrYImKiCzmDZvE-i93cePVQ4ODiuusHgk1vH5QgvPv62Sh-xxQPb4TsWj2G_RBoo9dFlg4zbWOdb9z6SVzR86ouxKOX_RhE4vWsReVD4ukdsW8eO7SVCI74qc61hIS12X6u-Hv40g"}

:Example of Response Data after Decryption:

::

	{"code":"0","data":{"id":48680,"status":0},"msg":"success"}
