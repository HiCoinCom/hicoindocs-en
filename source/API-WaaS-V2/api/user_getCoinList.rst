
2.4 获取支持的币列表
~~~~~~~~~~~~~~~~~~~~~~~~

:说明: 获取商户的币种列表
:接口地址: /api/v2/user/getCoinList
:请求方式: GET
:请求参数:

========= ========== ============= ===================================================
Param	    类型        是否必须       说明
app_id	  String	   可选	          商户唯一表示
data      String	   可选	          加密之后的字符串，解密之后的格式如下定义
========= ========== ============= ===================================================

:请求参数data解密之后数据结构:

========= ======= ========== ===================================================
Param     类型     是否必须     说明
time      long    必填	      当前时间戳
charset   String  必填        编码格式，无特殊情况，传参数utf-8
version   String  必填        接口版本号，无特殊情况，传参数v2
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

========== ======= =========== ====================================================
Param      类型     是否必须      说明
symbol     String  是           币种
icon       String  是           币种icon
========== ======= =========== ====================================================



:响应示例:

::

	{"data":"LK4D5mrtvTubDxCQM4lqyN2h8TTIkEBL_06FrrrzLrImyMO4Yuac-wdbk5VnGVfCKB5EFaUb162xXUJdTHhpA5CGBCAQKl64h_Dt10C-H8KIoap9dZI90qE4f-mAMAyjF1QzKXJ-f-R_3J3bRGqfHFBRXebh08R8MdRDssniopVOhsFUs4gBxUensKas3_ta15eFIqXPjIgJWfYQCD2DUi1gaKgmN-5Q_tgt-qXp5Y2uh3yfM4g4k71Ahyel3G8S_AktbWl2G9wU3cri3ZVQEo0faIpkX_CKsk9V1YoY5yRopvJbxNtkG9lBFxKnureAQo0KP3f1tsIMOzgcyEXPnA"}

:响应数据解密后示例:

::

	{
    "code":"0",
    "data":[
        {
            "symbol":"BTC",
            "icon":"http://chainup-oss.oss-cn-beijing.aliyuncs.com/saas/1565681771193.png"
        },
        {
            "symbol":"ETH",
            "icon":"http://hicoin.oss-cn-hongkong.aliyuncs.com/coin/1530015263780.png"
        },
        {
            "symbol":"BCH",
            "icon":"http://hicoin.oss-cn-hongkong.aliyuncs.com/coin/1530016466295.png"
        }
    ],
    "msg":"成功"
  }
