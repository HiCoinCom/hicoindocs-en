
2.13 用户提现和充值异步回调通知
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:说明: 此接口仅定义了接口规范，具体接口需要开发者实现
:接口地址: 接口地址由开发者提供，联系管理员在平台进行配置即可
:请求方式: POST
:请求参数:


========= ========== ============= ===================================================
Param	    类型        是否必须       说明
app_id	  String	   可选	          商户唯一表示
data      String	   可选	          加密之后的字符串，解密之后的格式如下定义
========= ========== ============= ===================================================


:请求参数data解密之后数据结构:

注意：提现通知与充值通知的数据结构有差异：

提现通知：

===================== ========== ============= ==========================================================================================
Param	                 类型        是否必须       说明
charset                String      是           编码格式，无特殊情况，传参数utf-8
version                String      是           接口版本号，无特殊情况，传参数v2
side                   String      是           通知类型， 充值通知：deposit， 提现通知： withdraw
notify_time            String      是           通知时间
request_id             String      是           提现请求ID，对应提现接口中的request_id
id                     String      是           提现id
uid                    String      是           提现用户id
symbol                 String      是           币种
amount                 String      是           提现金额
withdraw_fee_symbol    String      是           提现手续费币种
withdraw_fee           String      是           提现手续费
fee_symbol             String      是           挖矿手续费币种
real_fee               String      是           矿工费
address_to             String      是           充值地址
created_at             String      是           创建时间
updated_at             String      是           修改时间
txid                   String      是           区块链交易ID
confirmations          String      是           区块链确认数
status                 String      是           提现状态: 0 未审核，1 审核通过，2 审核拒绝，3 支付中已经打币，4 支付失败，5 已完成
===================== ========== ============= ==========================================================================================

充值通知：

===================== ========== ============= ===================================================
Param	                 类型        是否必须       说明
charset                String      是           编码格式，无特殊情况，传参数utf-8
version                String      是           接口版本号，无特殊情况，传参数v2
side                   String      是           通知类型， 充值通知：deposit， 提现通知： withdraw
notify_time            string      是           通知时间
id                     string      是           充值id
uid                    string      是           提现用户id
symbol                 string      是           币种
amount                 string      是           提现金额
address_to             string      是           充值地址
created_at             string      是           创建时间
updated_at             string      是           修改时间
txid                   string      是           区块链交易ID
confirmations          string      是           区块链确认数
status                 string      是           充值状态     0待确认，1 已完成，2 异常
===================== ========== ============= ===================================================



:请求参数示例:

::

  app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=UoJC0VeVSvdOCYbkUIQxnJ2k-MINFmdfhHo1bpgK1kqcCKEZ1MtBFmvMnrZsmpQKVyNbFyBmLHzOk_T5FTxKA0VROneKR4wyK0G6HPQM6pDeSz2BPwwaw-2uiBSiPeQEwOabWl0MLyoJyj1g4VLcBgazCYeD5YPJXFOzjAEgkhfbMEcoS1to_ooISnIMeQvhj8g3I3m5k519eJ9KWOv5R3_EGMaI-yLlCB5CIVd4byjnBxDJxsRMR7yuEhIjfvsy49MgglSTrddCFu3ZHNwGlv_DzTJIMhJHRV7z4x8YQV2atP-BBgY9eozPa0JIkjBctdqigvzJs5nsbl76wL5Gv5-icGv4qtOF0w11t0oPi051Y7fiuPJ20BK6GAPEu_HroTvcWh-3vh2_U03Donv306HMvC-vXrQH18TGVqjtOlVhQW_wg4PF9fjMgNCsk3k57vzVfuRruurLv6-FD6HRvoUe4WfgSAi-jMRpuwXC8mL44r-dLDfo4wUdrjEk8tkjSZea8O066bJeVVUU3rD7qqL32Uf-3Bkcy26jsHLf-QK8oYi2xjddd2PSoHnpSIbRdDYrYLdO_zUFZudg4FBHFzQ6sSLesS_jA63xJZS1xk6EjejaSpID3r-7YXDQtM3y5O1TG3URmF5sVbWL5iekubN2jEjkQ2QdV4hz0sBdmlx8GrPUWSnbtLMV7zcxAhyodzIeWeeZCKeu1AF903YJvKZls8eKMEvd__PYSnnRtXVxNUvFFo-GL3sOtDAAhjKdLLSWCVGqDQsKSrORffejbDeHVGsmtFxPC5kvKHLbJvAW6QDzpG8hqmZLrtjxvTmcVMt1_hn9-VSi-qFW8xPorYmF5Hw1G5nZca7NK5k2Qs6xieNgw34Sps-tj38WxhXacRwlEp1Yt3Jj3BlMlxCD9VWxWO17Yvj3MmJTNgf-d22PvPV_mZrJaqjm6BSfuz9DVYVjsIuZF_eOgMaVTm31FFuFZvPF9G_lhC4CQ0Zb5KfpYx0NMJjGfBPtxZ3MsF8H


:响应参数:

返回字符串：SUCCESS表示成功，FAILURE表示失败 （注意此处返回参数无需进行加密）
