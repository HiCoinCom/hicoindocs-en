1 Preparation
====================

1.1 Development
-------------------

1）Two Sets of Public & private Key Need
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**The first set of public and private keys**: The developer shall generate the first set of public and private key before opening an Asset Account. The public key (rsa_third_pub) will be provided to the platform and the private key need to be kept by yourself. Since the private key is the only proof for the third-party application to access into the wallet service, please do not disclose to anyone. When a third party sends a wallet service request, the parameter is encrypted by the private key, the platform will decrypt the request data by the public key provided (rsa_third_pub).

**The second set of public and private keys**: the platform will provide the wallet public key (RSA_wallet_pub) to the developer after they opens the asset account. The public key is required to be used for decryption when the third-party application receives the response data or asynchronous notification from the wallet

2）Why need to confirm the withdrawal twice
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In order to confirm the request is legitimate applied by a third party when it is received by the wallet, the interface provided by the third party will be invoked to confirm. Somehow, this process can avoid the impact caused by the loss of the private key of the third party, and also provides an effective barrier for the security of wallet service.



1.2 Prepare the account
-------------------

The developer needs to prepare: 

1) Generate a set of public and private keys to provide the public key only to the platform; 

2) IP of third-party application server; 

3) Deposit and withdrawal callback notification address; 

4) Confirm the address of withdrawal for the second time; 

5) Whether to turn on the automatic collection features. Once turn it on, the system will automatically transfer the user's prepaid funds to the merchant collection account. 

Contact customer service of the platform to provide the above five listed information. The platform will setup your Assets Management Account as well as the 

1) The unique identity of the merchant: app_id; 

2) Wallet public key: rsa_wallet_pub.


1.3 Introduction
-------------------

The document is the interface provided by the wallet service to third-party applications.

.. image:: images/apiopen-instructions.png
   :width: 450px
   :height: 153px
   :align: center

The interface providers in the following are called **wallet services** and the interface invoking are called **third-party applications**. When the third-party application requests the wallet service, it encrypts the request parameters through RSA algorithm, and decrypts the response data after receiving the wallet service



1.4 Interface Rules
-------------------------
:Method: https(The test environment is used temporarily http)
:Sign: Apart from the “Sign”, all mandatory fields require signatures on it. 
:Status Code: “0 “indicates successful processing, while “ non-0” indicates request error or system exception 
:Reuest URL: Domain name + interface address
:Encryption: See Appendix 1 
