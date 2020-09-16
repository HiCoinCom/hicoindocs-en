
2.13 User Withdrawal and Deposit Asynchronous Callback Notification
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:NOTE: This document defines the specification, the specific interface needs to be implemented by the developer
:URI: The interface address is provided by the developer and then configured on the WaaS platform
:Method: POST
:Request Parameters:

=========== =========== =========== =====================================================================================================================
Params	    Type        Required 	  Description
app_id      String      Y           app id
data        String      Y           The request parameters after encryption and the data structure after decryption are defined as follows
=========== =========== =========== =====================================================================================================================

:Data Structure After Request Parameter Data Decryption:

:NOTE: The data structure of withdrawal notification and deposit is different

:Withdrawal data structure:

===================== =========== =========== ====================================================================================
Params	              Type        Required	  Description
side                  String      Y           Notification type, deposit notification: deposit, withdrawal notification: withdraw
charset               String      Y           Encoding format, default parameter utf-8
vesion                String      Y           api vesion, default parameter v2
notify_time           String      Y           Notification time
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
status                int         Y           0 Unreviewed, 1 Reviewed，2 Review Rejected，3 Processing，4 failture, 5 complete
===================== =========== =========== ====================================================================================

:Deposit Data Structure:

============== =========== =========== ===========================================================================================
Params         Type        Required    Description
side           String      Y           Notification type, deposit notification: deposit, withdrawal notification: withdraw
charset        String      Y           Encoding format, default parameter utf-8
vesion         String      Y           api vesion, default parameter v2
notify_time    String      Y           Notification time
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
============== =========== =========== ===========================================================================================

:Example of Request Parameter:

::

  app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=UoJC0VeVSvdOCYbkUIQxnJ2k-MINFmdfhHo1bpgK1kqcCKEZ1MtBFmvMnrZsmpQKVyNbFyBmLHzOk_T5FTxKA0VROneKR4wyK0G6HPQM6pDeSz2BPwwaw-2uiBSiPeQEwOabWl0MLyoJyj1g4VLcBgazCYeD5YPJXFOzjAEgkhfbMEcoS1to_ooISnIMeQvhj8g3I3m5k519eJ9KWOv5R3_EGMaI-yLlCB5CIVd4byjnBxDJxsRMR7yuEhIjfvsy49MgglSTrddCFu3ZHNwGlv_DzTJIMhJHRV7z4x8YQV2atP-BBgY9eozPa0JIkjBctdqigvzJs5nsbl76wL5Gv5-icGv4qtOF0w11t0oPi051Y7fiuPJ20BK6GAPEu_HroTvcWh-3vh2_U03Donv306HMvC-vXrQH18TGVqjtOlVhQW_wg4PF9fjMgNCsk3k57vzVfuRruurLv6-FD6HRvoUe4WfgSAi-jMRpuwXC8mL44r-dLDfo4wUdrjEk8tkjSZea8O066bJeVVUU3rD7qqL32Uf-3Bkcy26jsHLf-QK8oYi2xjddd2PSoHnpSIbRdDYrYLdO_zUFZudg4FBHFzQ6sSLesS_jA63xJZS1xk6EjejaSpID3r-7YXDQtM3y5O1TG3URmF5sVbWL5iekubN2jEjkQ2QdV4hz0sBdmlx8GrPUWSnbtLMV7zcxAhyodzIeWeeZCKeu1AF903YJvKZls8eKMEvd__PYSnnRtXVxNUvFFo-GL3sOtDAAhjKdLLSWCVGqDQsKSrORffejbDeHVGsmtFxPC5kvKHLbJvAW6QDzpG8hqmZLrtjxvTmcVMt1_hn9-VSi-qFW8xPorYmF5Hw1G5nZca7NK5k2Qs6xieNgw34Sps-tj38WxhXacRwlEp1Yt3Jj3BlMlxCD9VWxWO17Yvj3MmJTNgf-d22PvPV_mZrJaqjm6BSfuz9DVYVjsIuZF_eOgMaVTm31FFuFZvPF9G_lhC4CQ0Zb5KfpYx0NMJjGfBPtxZ3MsF8H


:Response Parameters:

"SUCCESS" means success, FAILURE means failure

:NOTE: The parameters returned need to be encrypted
