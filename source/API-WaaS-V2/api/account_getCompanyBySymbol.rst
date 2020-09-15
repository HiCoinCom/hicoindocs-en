
2.6 Get the Merchant's Aggregate Account Balance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:URI: /api/v2/account/getCompanyBySymbol
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
symbol      String       Y          symbol
=========== =========== =========== ============================================

:Example of Request Parameter:

::

	app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=YepWL0rl-SK3qhhHrH-Nk-0ohFqkhV33cLXRHHmIIDJ1GJbfy5aUHWxrG342gxkPvdQF-Hnq3ajez2eqrJIisNCXiUw7-f2TgXUdSlShGF-6I7QeSinclCbKj-sqsRpRS9lFFTGWz-GUuUJiWkgK6mCsEH3xMKM-14nHKU6R1K7lbsPMn61E4P8lxtkWs9uwB97hHADzSJswXF-jTCqY2xYZDILXQTm6wwMFVL3ynIV9YWosprAVOrkQ9hawxRl9vmJDvF85JI8qNaNMcmwlLNzBPLdeQJHjRTEkj2BtiNk3gU8IYAWifwVv0alFb8zrVIJbEm4S_GfybB2oOzNmOQ

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
balance           String      Y           balance
================= =========== =========== =========================================================

:Example of Response Data:

::

	{"data":"jwtkGrhh2EVJS8xe93MpUYd-SQ-TyK0Bx5sXjE4hygFNg4wmctiahtIYXRpR2j8yDaEF5YzVstnUKbOH2p44FSMjXMQU4qFrhD00WOfW7v4LNALyiQXRb_5sakR0Zf573lGfLRTPlzLtTho3gqu3hMwuAv5e3r2dpb6_jxh1Z9BjkzSsNRX_bjLcHLUOPhMvo6rTUKSa9LQ6QnT8RX0eqzOZPlnCw3TeX_zcWWjxp6fcpKcdODxoI86gHwWRpSd-2qbEbFcaT12CJd9nPXA0KnLPNNHWz8sxQGiAg7Jg_-cN_yBHL9cS15zecTemYGqpOXRkojM1JwLsjM-7txf_dw"}


:Example of Response Data after Decryption::Example of Request Parameter:

::

	{"code":"0","data":{"symbol":"ETH","balance":"64.97599802"},"msg":"success"}
