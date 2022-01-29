1 Preliminary Preparation
====================

1.1 Development Notes
-------------------

The Role of Public and Private Keys
~~~~~~~~~~~~~~~~~~~

Party A is a third-party public chain docking party

Party B is the WaaS Alliance BaaS Cloud

**The Role of Public and Private Keys**： Party A needs to generate a pair of public and private keys in advance when registering the WAPI interface. The public key (rsa_third_pub) is provided to Party B. The private key is kept by yourself, and the private key is not disclosed to anyone. When requesting WAPI services, Party A shall encrypt the request parameters with Party B's public key and sign the original data after MD5 with Party A's private key. Upon receiving the request, Party B shall decrypt the data with Party B's private key and check the original data after MD5 with Party A's public key



1.2 Account Preparation
-------------------

Developers need to prepare the following information：

1）Generate a pair of public and private keys, and provide the public key to the platform；

2）Third-party application server IP；


Contact the relevant people of the platform and provide the above two types of information. The platform prepares WAPI docking information for you, and provides you with the following information：

1）The unique identifier for third-party docking: app_id；

2）WAPI public key：rsa_wapi_pub。

:RSA public and private key generation address:

http://www.metools.info/code/c80.html

Password length：2048

Key format：PKCS#8


1.3 Interface rules
--------------
:Transmission method: https (the test environment temporarily uses http)
:Signature Field: Except for the sign field, all other required fields need to be signed
:The response status code: 0, indicating successful processing;non-zero, indicating request error or system abnormality
:Request Address: domain name + interface address
:Encryption Algorithm: See Appendix 1 for details
