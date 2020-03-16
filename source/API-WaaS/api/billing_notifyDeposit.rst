
2.17 Asynchronous Callback Notification of Deposit Results
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
id                     string  Y               deposit record unique identifier
uid                    string  Y               user id
symbol                 string  Y               symbol
amount                 string  Y               deposit amount
address_to             string  Y               deposit address
created_at             string  Y               create time
updated_at             string  Y               update time
txid                   string  Y               transaction id in blockchain
confirmations          string  Y               confirmations in blockchain
status                 string  Y               deposit status, 0:waiting for confirmation，1: complete 2: failure
====================== ======= =============== ====================================================================================

:Response Parameters:

'SUCCESS' means OK, 'FAILURE' means 'notification failed'
