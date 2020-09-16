2.9 Sync User's Withdrawal Records
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:URI: /api/v2/billing/syncWithdrawList
:Method: GET
:Request Parameters:

=========== =========== =========== =====================================================================================================================
Params	    Type        Required 	  Description
app_id      String      Y           app id
data        String      Y           The request parameters after encryption and the data structure after decryption are defined as follows
=========== =========== =========== =====================================================================================================================

:Data Structure After Request Parameter Data Decryption:

=========== =========== =========== ==============================================================
Params	    Type         Required   Description
time        long         Y          timestamp
charset     String       Y          Encoding format, default parameter utf-8
vesion      String       Y          api vesion, default parameter v2
max_id      int          Y          The maximum id of the data returned by the last request
=========== =========== =========== ==============================================================

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

===================== =========== =========== ====================================================================================
Params	              Type        Required	  Description
request_id            String      Y           unique ID for each HTTP request
id                    int         Y           withdrawal record id
uid                   int         Y           user id
symbol                String      Y           symbol name
amount                String      Y           withdrawal amount
withdraw_fee_symbol   String      Y           withdrawal fees symbol
withdraw_fee          String      Y           withdrawal fees
fee_symbol            String      Y           mining symbol
real_fee              String      Y           miner fee
created_at            String      Y           created time
updated_at            String      Y           updated time
address_to            String      Y           withdrawal address
txid                  String      Y           transaction id in blockchain
confirmations         int         Y           confirmations in blockchain
saas_status           int         Y           status of platform review
company_status        int         Y           status of merchant review
status                int         Y           0 Unreviewed, 1 Reviewed，2 Review Rejected，3 Processing，4 failture, 5 complete
===================== =========== =========== ====================================================================================


:Example of Response Data:

::

	{"data":"LK4D5mrtvTubDxCQM4lqyN2h8TTIkEBL_06FrrrzLrImyMO4Yuac-wdbk5VnGVfCKB5EFaUb162xXUJdTHhpA5CGBCAQKl64h_Dt10C-H8KIoap9dZI90qE4f-mAMAyjF1QzKXJ-f-R_3J3bRGqfHFBRXebh08R8MdRDssniopVOhsFUs4gBxUensKas3_ta15eFIqXPjIgJWfYQCD2DUi1gaKgmN-5Q_tgt-qXp5Y2uh3yfM4g4k71Ahyel3G8S_AktbWl2G9wU3cri3ZVQEo0faIpkX_CKsk9V1YoY5yRopvJbxNtkG9lBFxKnureAQo0KP3f1tsIMOzgcyEXPnA"}

:Example of Response Data after Decryption:

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
