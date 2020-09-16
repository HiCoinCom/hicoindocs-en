
2.12 Batch Get Deposit Records
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:URI: /api/v2/billing/depositList
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
ids         String       Y	        multiple 'id' are separated by commas, up to 100 id
=========== =========== =========== ==============================================================

:Example of Request Parameter:

::

	app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=L-GwqoS2NJAOIUHMM5NAqJJvBKxWLjANyh1UHRvQbFUCHfzJBxEpGi514sI_J051wO4QMK9xeZK6_f7p_CIQfVJ7kiq7FNmflHnyjPT9tGdL6h7GSnHcPFEUUyHA7hJlvt3BtPyYuaEN9s1cJ1c8DzlOLTnzRF5EiPPrw-Yq0wtBYORIjEtfOBEMChF5vxu-FIjb3Nx4usIeWEamkC5WpkjRcjPZlE7-pRnA59fgHMtA3-hvsxJYwhCKLFkq-fAPfpTf4IpgZWdmrCEfGAdExSDCoQVNEJZgZnonzy5bDsUBQIRWuJZbO5u0JYnjdBliqpOi_L6j_chbe_er2eT5_w

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

============== =========== =========== ==================================================================================
Params         Type        Required    Description
id             int         Y           deposit record id
uid            int         Y           user id
symbol         String      Y           symbol name
amount         String      Y           deposit amount
created_at     String      Y           create time
updated_at     String      Y           update time
txid           String      Y           transaction id in blockchain
confirmations  int         Y           confirmations in blockchain
address_to     String      Y           deposit address
status         int         Y           deposit status, 0:waiting for confirmation，1: complete 2: failure
============== =========== =========== ==================================================================================

:Example of Response Data:

::

	{"data":"T1IaOzF2XfNaAOb3XqSFxCq6nu45SpiD9anDIlxHda_lOwX2kNNAl84OOsVnAsMg4IBQICD6_PMglpU5InzL_Q1AoNf_l1kPlk_fMXvmpEz25OAVJ499UYmBpH83TQclFfsxPKaFhIgeNGYgVGaS3BdT4Z0EBmfbMAz9aTa4n5z9Ns4q4b6En030GLINhC8PmaEQ5PDq5ZXZTKiKSrRNpNRi3_FR8hdIJGOLFU6t1Yb2nxqB1D-fY6eRtSHQnCCyas73kj-_kAhyW4dGss7vqKQZPmDe38qSYPrQUoDlJgK_8aCKG8fvJmoC9s3-o3InALAGp3yOawn32E1AxZtNbDQcUux6xbyAhhIOBhyN_V2LPR9yOtJQvm3XbdMxk58i-Y6oZl_YtBdfRncvhDJnAPqP3MN4sdbuC3JaC19bKikTDykXzFgD2_rHN4CO8QHUAefRAm-x9hj_sHFOwrJdL9g1H2Auzz1cES4zcp5RKHsduFnUNlvoKRNl9SUuIbDahTtBHlF1Gw9xy1my9KMB2X-u1vvnL83hvp4Rqnz0SyMfnpEnqRph43cCiyj7Ii3cf-Ai8h2i-5yIqr2qDKJoL5GqaOu6hr5atO4IZXZPzY175wZ4nNpCueBXRHoWB2foVmLu_F6xwq06XKDR9U5JYln3iol9DX2OhqM0Bs8cPqw"}

:Example of Response Data after Decryption:

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
