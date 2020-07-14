
2.7 获取用户指定币账户地址
~~~~~~~~~~~~~~~~~~~~~~~~~~~

:说明: 获取用户指定币账户地址。如果没有地址，则给用户分配一个地址，此时不应生成账户，账户还是按需生成。
:接口地址: /api/v2/account/getDepositAddress
:请求方式: POST
:请求参数:


========= ========== ============= ===================================================
Param	    类型        是否必须       说明
app_id	  String	   可选	          商户唯一表示
data      String	   可选	          加密之后的字符串，解密之后的格式如下定义
========= ========== ============= ===================================================

:请求参数data解密之后数据结构:

========= ======= ========== ===================================================
Param     类型     是否必须     说明
time      long    必填        当前时间戳
charset   String  必填        编码格式，无特殊情况，传参数utf-8
vesion    String  必填        接口版本号，无特殊情况，传参数v2
uid       String  必填	      用户ID
symbol    String  必填	      币种
========= ======= ========== ===================================================


:请求参数示例:

::

	app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=GCJBk77n7epyOexdGZ20qvukd321TpJ62lIAtlCinW6TzHx8SIbm6evXGulO87UgLTzIWCtgupgeLJKDdZmC7msuPNBGK--Ec27WZXjuhI0gNWXcOVk5RW_VRVcyfJ1Ml-DMW8XVxZRgA2U1bt9BztiyfryzMGj8_jl1IXd5sOQfPYXulCdm70WyTJpjsDkuMSov6QUmOn-C_-HUoZ7s715EMeZ60D09uUsF0i6mKLhFZTEQZPGPeJITYSJNddAw7nvqvX2KzNc6YUeCQhEmU1Dfxp65W4e3SVOgpd_2Q-dLN1MpOlkUKwbmbpb-gEh_s68yl7ox6WSgKfCK4i_uvA


:响应参数:

========= ========== ============= ===================================================
Param	    类型        是否必须       说明
data      String     可选           加密之后的字符串，解密之后的格式如下定义
========= ========== ============= ===================================================


:响应参数data解密之后:

========= ========== ============= ===================================================
Param	    类型        是否必须        说明
code	    String     是	           状态码
msg       String     是             响应结果说明
data      String     否             具体响应数据，数据结构定义如下
========= ========== ============= ===================================================

:data数据结构:

========= ========= ============= ===================================================
Param      类型      是否必须        说明
uid        int      是             用户在钱包服务的唯一标识
address    String   是             币种账户地址
========= ========= ============= ===================================================



:响应示例:

::

	{"data":"C6vPlXILSVMFOY4yzXMQ3lNmNRLbnfCIlIwgRXo3UXH152rKma-9vq8dEomWNOOhCxhsW-cV7bh1SpYQg2ehK5QbcIbrCdIyuD87QPyAUnXn5UgEWcYQU_6stj8yazgv5o6QfAZbe5AUDs4rjU55NziDI0Ml9bbpkk1u9PhH8L5s2uoYjjDkjTqk_KQx9Mjt42VvDkfaWUuAsaF3V0uqaCVEvnx0yQXS_lr4zRsNptspnHGJwXnvhBMRN3EEkpG_IdlkndK3Lujwe96vlqPQawLE1nDE7VsPwJq-4S-2GHOtUPMzdBXAGIHnDFeMT03ExXWBMWutng89itdFR6zRUg"}

:响应数据解密后示例:

::

	{"code":"0","data":{"uid":"3529218","address":"0x6956f9af53b22117f2fc94dfe7c74ff3893b2acd"},"msg":"成功"}
