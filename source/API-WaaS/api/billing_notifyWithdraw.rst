
2.16 Asynchronous Callback Notification of Withdrawal Results
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:Description: Only interface specifications are defined, and specific interfaces need to be implemented by developers
:URI: 'URI' is provided by the developer, and the administrator can configure it on the platform
:Method: POST
:Request Parameters:

====================== ======= =============== ====================================================================================
Params	               Type    Required	       Description
app_id                 string  Y               app id
charset                string  Y               charset
version                string  Y               version
notify_time            string  Y               notify time
id                     string  Y               withdrawal record unique identifier
uid                    string  Y               user id
symbol                 string  Y               symbol
amount                 string  Y               withdrawal amount
withdraw_fee_symbol    string  Y               withdrawal fees symbol
withdraw_fee           string  Y               withdrawal fees
fee_symbol             string  Y               mining symbol
real_fee               string  Y               miner fee
address_to             string  Y               withdrawal address
created_at             string  Y               create time
updated_at             string  Y               update time
txid                   string  Y               transaction id in blockchain
confirmations          string  Y               confirmations in blockchain
status                 string  Y               0 Unreviewed, 1 Reviewed，2 Review Rejected，3 Processing，4 failture, 5 complete
====================== ======= =============== ====================================================================================

:Response Parameters:

'SUCCESS' means OK, 'FAILURE' means 'notification failed'
