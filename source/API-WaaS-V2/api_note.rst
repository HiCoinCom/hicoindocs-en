
4 Appendix
==============

Appendix 1 : Encryption and decryption
~~~~~~~~~~~~~~~~~~~~~~~~

The values of the request parameter data and response field data are the result of RSA encryption and base64urlsafe encryption.

*Attention*

1）In traditional base64 encoding “+” and “ /” will be directly escaped by URL, so if we want to transfer these encoded strings through URL, we need to do traditional Base64 encoding first, then replace “+ ”and “/ ” to be “-_ ”characters respectively, and do the opposite action decoding at the receiving end

2）rsa encryption and decryption using segment encryption

:Example of request parameter encryption:

::

	 // Origin data
	 String originReqData = '{"charset":"utf-8","symbol":"eth","sign":"","time":"1586420916306","app_id":"baaceb1e506e1b5d7d1f0a3b1622583b","version":"2.0"}'

	 // encryptByPrivate方法封装在下列公共类RSAHelper.java中
	 String encryptReqData = RSAHelper.encryptByPrivate(originReqData, "第三方自己的私钥")

	 //http post
	 String httpBuildParams = "app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data=" + encryptReqData



:响应数据解密示例:

::

	// 响应的原始数据
  String originResp= '{"data":"jwtkGrhh2EVJS8xe93MpUYd-SQ-TyK0Bx5sXjE4hygFNg4wmctiahtIYXRpR2j8yDaEF5YzVstnUKbOH2p44FSMjXMQU4qFrhD00WOfW7v4LNALyiQXRb_5sakR0Zf573lGfLRTPlzLtTho3gqu3hMwuAv5e3r2dpb6_jxh1Z9BjkzSsNRX_bjLcHLUOPhMvo6rTUKSa9LQ6QnT8RX0eqzOZPlnCw3TeX_zcWWjxp6fcpKcdODxoI86gHwWRpSd-2qbEbFcaT12CJd9nPXA0KnLPNNHWz8sxQGiAg7Jg_-cN_yBHL9cS15zecTemYGqpOXRkojM1JwLsjM-7txf_dw"}'

	// 解密响应数据
	String encryptRespData = JSON.parse(originResp)['data']
	// decryptByPublic 方法封装在下列公共类 RSAHelper.java中
  String decryptRespData = RSAHelper.decryptByPublic( encryptRespData, "托管平台提供的公钥" )


:公共类RSAHelper.java:

::

	import org.apache.commons.codec.binary.Base64;
	import org.apache.commons.lang3.StringUtils;

	import sun.misc.BASE64Decoder;
	import sun.misc.BASE64Encoder;
	import sun.security.rsa.RSAPrivateCrtKeyImpl;

	import javax.crypto.Cipher;
	import java.io.ByteArrayOutputStream;
	import java.security.*;
	import java.security.interfaces.RSAPrivateKey;
	import java.security.interfaces.RSAPublicKey;
	import java.security.spec.PKCS8EncodedKeySpec;
	import java.security.spec.RSAPublicKeySpec;
	import java.security.spec.X509EncodedKeySpec;
	import java.util.*;

	@SuppressWarnings("restriction")
	public class RSAHelper {
		/**
		 * 加密算法RSA
		 */
		public static final String KEY_ALGORITHM = "RSA";

		/** *//**
		 * RSA最大加密明文大小
		 */
		private static final int MAX_ENCRYPT_BLOCK = 234;

		/** *//**
		 * RSA最大解密密文大小
		 */
		private static final int MAX_DECRYPT_BLOCK = 256;


		private static final String CHARSET ="UTF-8";



		/**
		 * 公钥解密
		 *
		 * @param encryptedData 已加密数据
		 * @param publicKey 公钥(BASE64编码)
		 * @return
		 * @throws Exception
		 */
		public static byte[] decryptByPublicKey(byte[] encryptedData, String publicKey)
				throws Exception {
			byte[] keyBytes =  (new BASE64Decoder()).decodeBuffer(publicKey);
			X509EncodedKeySpec x509KeySpec = new X509EncodedKeySpec(keyBytes);
			KeyFactory keyFactory = KeyFactory.getInstance(KEY_ALGORITHM);
			Key publicK = keyFactory.generatePublic(x509KeySpec);
			Cipher cipher = Cipher.getInstance(keyFactory.getAlgorithm());
			cipher.init(Cipher.DECRYPT_MODE, publicK);
			int inputLen = encryptedData.length;
			ByteArrayOutputStream out = new ByteArrayOutputStream();
			int offSet = 0;
			byte[] cache;
			int i = 0;
			// 对数据分段解密
			while (inputLen - offSet > 0) {
				if (inputLen - offSet > MAX_DECRYPT_BLOCK) {
					cache = cipher.doFinal(encryptedData, offSet, MAX_DECRYPT_BLOCK);
				} else {
					cache = cipher.doFinal(encryptedData, offSet, inputLen - offSet);
				}
				out.write(cache, 0, cache.length);
				i++;
				offSet = i * MAX_DECRYPT_BLOCK;
			}
			byte[] decryptedData = out.toByteArray();
			out.close();
			return decryptedData;
		}

		/**
		 *  公钥分段解密
		 * @param encryptedData 加密的base64数据
		 * @param publicKey rsa 公钥
		 * @return
		 */
		public static String decryptByPublicKey(String encryptedData, String publicKey){
			if(StringUtils.isBlank(encryptedData) || StringUtils.isBlank(publicKey)){
				return "";
			}

			try {
			    encryptedData = encryptedData.replace("\r", "").replace("\n", "");
	            Base64 decoder = new Base64(true);
				byte[] data = decryptByPublicKey(decoder.decode(encryptedData), publicKey);
				if(data == null || data.length < 1){
					return  "";
				}
				return new String(data);
			}catch (Exception ex){
				ex.printStackTrace();
			}
			return "";
		}

		/**
		 * 私钥加密
		 *
		 * @param data 源数据
		 * @param privateKey 私钥(BASE64编码)
		 * @return
		 * @throws Exception
		 */
		public static byte[] encryptByPrivateKey(byte[] data, String privateKey)
				throws Exception {
			byte[] keyBytes =  (new BASE64Decoder()).decodeBuffer(privateKey);
			PKCS8EncodedKeySpec pkcs8KeySpec = new PKCS8EncodedKeySpec(keyBytes);
			KeyFactory keyFactory = KeyFactory.getInstance(KEY_ALGORITHM);
			Key privateK = keyFactory.generatePrivate(pkcs8KeySpec);
			Cipher cipher = Cipher.getInstance(keyFactory.getAlgorithm());
			cipher.init(Cipher.ENCRYPT_MODE, privateK);
			int inputLen = data.length;
			ByteArrayOutputStream out = new ByteArrayOutputStream();
			int offSet = 0;
			byte[] cache;
			int i = 0;
			// 对数据分段加密
			while (inputLen - offSet > 0) {
				if (inputLen - offSet > MAX_ENCRYPT_BLOCK) {
					cache = cipher.doFinal(data, offSet, MAX_ENCRYPT_BLOCK);
				} else {
					cache = cipher.doFinal(data, offSet, inputLen - offSet);
				}
				out.write(cache, 0, cache.length);
				i++;
				offSet = i * MAX_ENCRYPT_BLOCK;
			}
			byte[] encryptedData = out.toByteArray();
			out.close();
			return encryptedData;
		}

		/**
		 *  私钥分段加密数据
		 * @param data 待加密数据
		 * @param privateKey  私钥
		 * @return
		 */
		public static String encryptByPrivateKey(String data, String privateKey){
			if(StringUtils.isBlank(data) || StringUtils.isBlank(privateKey)){
				return "";
			}

			try {
				byte[] encryptedData = encryptByPrivateKey(data.getBytes("UTF-8"), privateKey);
				if(encryptedData == null || encryptedData.length < 1){
					return  "";
				}

	            Base64 encoder = new Base64(true);
	            byte[] dataBytes = encoder.encode(encryptedData);
	            return new String(dataBytes).replace("\r", "").replace("\n", "");
			}catch (Exception ex){
				ex.printStackTrace();
			}
			return "";
		}

  }


:PHP签名Demo:

::

	<?php
		class RSA
		{

			//第三方私钥
		    public $pri_key = 'MIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIBAQD6YNILWOJZjS6FQQ9ZL9CEKcWZTTldrDLsxP2dQME7hSUTDQ5AosBUZk18Uq212SC2+L0UA9G6WPoCNzHCB8TP25jC+EwIkHMN4EEPRs+bEHUgX3Bq3oR2SCHjEiqleTFW2kO/oS6Vg9bhTST5MFaEnA0fc2Bh3+4iRus+5mVc6ux0lG55f1qmvUNM4hhP7qVpzc3X0xFA0Slu8dyel1dbOUQlJbUkrt5NzXXqmRoP5UVHUCXPZzH1kbxdbGA58TonXceh6DHQRa6pIBNaQ6BfnqhMvGVvuIqKPrdWq8yigvTw2zqBfwCwY3/3FZoI5ICQ8oS3GRHYP/rXzncqkKTzAgMBAAECggEAdag77EMnkueKXeo12TZj6Udr6N9mPsOl5qenelcsttiZlHtFIFCays6MSQjdQqA3BGSdDaPB0azwR0xCoKhf70GFZtGhgUDIIFQqnpArDPZN5BmVTVMlsiOxcPBfhAUQj3zf61RF/NLIjnVfE46IiaZ/cDEasMO3NvpWn+dK6L86zklgwHfC5IXTFnFRVA3bWkAQ3gswhLzjs50HNoNV96fsnbt1n7NSWhyz9B8hGMV+qYz1NGmb+VsaAune+oIv28krcaqf+Doah37rCmzEgVeZZ1/flPFOXpaq1eGJDgbLu6FbbgqfabCBlhmuzuwNbDl/2T/U9U6JoQWGR7t++QKBgQD8XSzBqpWwz8ebfsPipvnhIugbHgBnwLaRc3/xieuNuiDMsYPY1isBWSeYqjwV5uTad9s9dRxb6OOMH+KChkUxkYhEvoujUulGSuO4MxJlWl99WWEsbLzefubBD0zyHo5daHbPPXO8UPMu/SfiYxT2D5wsW2/swUqHWS3AmDS9RQKBgQD9/FJC/++DLyhU60Q9vrVY50zQTyPLtPnuIxbsPXB1Exo1wKe+LC02k9Cub9f5EFViTEniWRasB7ecnDxJT/ISU+hJjMUKFuaHueb7dO6wiIqyfpJeQM/4fKalBQI+nCEh3aceNKP44mk/lv2x22+P47EAKh7yqBdEVUv5GlHw1wKBgQCbAqReJOijXU0vLtMlYgj0h9tn5Kq9D/tUJky9UUkVmfFRqevhgdOSlW+j71TO4y9JHfvVqRyNO+ShCmi4Yb8Yrlq0VxIwdNoCqjdryjsPdE5ZEVCF2Bi+1dXpWfuacLhjman4q7duQY7OGwOno9KZPYdhG50JIMUlk9pthVBHvQKBgCXUC+iAuAqg3m/vboWHvvjT0mQANYOkm8j1HvfmmrZFNxUkcZdoev9y+pTQgalN3nm6hRKaVD8hEx7XQj9lEdfa+XDi74H2MTWr4ZQ4MUjHvWiiY2h4XMFUx3kyisgKdwDVQ4vDKVzrU+OtuHFiDnau4fD1VRCtKnH6Bku+uM+XAoGAB7V/OFlk7gaX7gne7p+DypXICn1oGE46aFLsDciOyePNovYg6bfdiUB9evwFSijiHq7eldZIQSRIdUalL1qfv2zDwFmEGpSd/RZYOOv21c3eISjln6W7ZGtumtLHx2nGpC072i5vNee0aAPEdvO0h3y4gvzad5L4KwIwyHifKic=';

			//钱包给的公钥
		    public $pub_key = 'MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAua4XMw/W9BxyZhirTlNau5Y/tdAHkPsbZo58Cdz1ByeRX8RwOibpREDZLTwhMTZGroqWEAZ+efQhx0gez++03Sw6IsPWPDpzpM90ezn2gBqPog7jxQA+M0E32gMHWB5ygplPwQkGz/qGYeJ5qhp2OZ8O+jFqOJNi7ob1hE2QsPT118HIhUzTL77urD61BovI+jg9Rx6PGAqlFLLmfXToqDulLkYVKhhQlL7ii6iuzIXgl46mbmvH2RXJRq083sa9b9J1z/WzXxNaHNpq5USl3ifTTyD/IiOKnblA7f4KJmr9rcMFbAP1mNxz95at6hPBvqGypPqqixxPBrdkOIPUVwIDAQAB';

			public function __construct() {

		        if (!is_null($this->pub_key)) {
		            $this->pub_key = openssl_pkey_get_public($this->formatterPublicKey($this->pub_key));
		        }

		        if (!is_null($this->pri_key)) {
		            $this->pri_key = openssl_pkey_get_private($this->formatterPrivateKey($this->pri_key));
		        }

		    }


			 /**
		     * 格式化公钥
		     * @param $publicKey string 公钥
		     * @return string
		     */
		    public function formatterPublicKey($publicKey)
		    {
		        if (false !== strpos($publicKey, '-----BEGIN PUBLIC KEY-----')) return $publicKey;

		        $str = chunk_split($publicKey, 64, PHP_EOL);//在每一个64字符后加一个\n
		        $publicKey = "-----BEGIN PUBLIC KEY-----".PHP_EOL.$str."-----END PUBLIC KEY-----";

		        return $publicKey;
		    }

		    /**
		     * 格式化私钥
		     * @param $privateKey string 公钥
		     * @return string
		     */
		    public function formatterPrivateKey($privateKey)
		    {
		        if (false !==strpos($privateKey, '-----BEGIN RSA PRIVATE KEY-----')) return $privateKey;

		        $str = chunk_split($privateKey, 64, PHP_EOL);//在每一个64字符后加一个\n
		        $privateKey = "-----BEGIN RSA PRIVATE KEY-----".PHP_EOL.$str."-----END RSA PRIVATE KEY-----";

		        return $privateKey;
		    }

			/**
		     * URL base64解码
		     * '-' -> '+'
		     * '_' -> '/'
		     * 字符串长度%4的余数，补'='
		     * @param unknown $string
		     */
		  function urlsafe_b64decode($string) {
		        $data = str_replace(array('-','_'),array('+','/'),$string);
		        $mod4 = strlen($data) % 4;
		        if ($mod4) {
		            $data .= substr('====', $mod4);
		        }
		        return base64_decode($data);
		    }

		    /**
		     * URL base64编码
		     * '+' -> '-'
		     * '/' -> '_'
		     * '=' -> ''
		     * @param unknown $string
		     */
		    function urlsafe_b64encode($string) {
		        $data = base64_encode($string);
		        $data = str_replace(array('+','/','='),array('-','_',''),$data);
		        return $data;
		    }


		    /**
		     *  私钥加密（分段加密）
		     *  emptyStr    需要加密字符串
		     */
		    public function encrypt($str) {
		        $crypted = array();
		//        $data = json_encode($str);
		        $data = $str;
		        $dataArray = str_split($data, 234);
		        foreach($dataArray as $subData){
		            $subCrypted = null;
		            openssl_private_encrypt($subData, $subCrypted, $this->pri_key);
		            $crypted[] = $subCrypted;
		        }
		        $crypted = implode('',$crypted);
		        return $this->urlsafe_b64encode($crypted);
		    }

		    /**
		     *  公钥解密（分段解密）
		     *  @encrypstr  加密字符串
		     */
		    public function decrypt($encryptstr) {
		        // echo $encryptstr;exit;
		        $encryptstr = $this->urlsafe_b64decode($encryptstr);
		        $decrypted = array();
		        $dataArray = str_split($encryptstr, 256);

		        foreach($dataArray as $subData){
		            $subDecrypted = null;
		            openssl_public_decrypt($subData, $subDecrypted, $this->pub_key);
		            $decrypted[] = $subDecrypted;
		        }
		        $decrypted = implode('',$decrypted);
		        // openssl_public_decrypt(base64_decode($encryptstr),$decryptstr,$this->pub_key);
		        return $decrypted;
		    }

		}
		$rsa = new RSA();
		$params = '{"charset":"utf-8","country":"+86","sign":"","mobile":"","time":"1589013592078","app_id":"baaceb1e506e1b5d7d1f0a3b1622583b","version":"2.0","email":"test123@qq.com"}';

		//加密参数
		$encryptParamsByPriv = $rsa->encrypt($params);

		//请求接口
		$resp = file_get_contents('http://awstestopenapi.hicoin.one/api/v2/user/info?app_id=baaceb1e506e1b5d7d1f0a3b1622583b&data='.$encryptParamsByPriv);

		$resp = json_decode($resp, true)['data'];
		//解密接口返回
		echo "get user info api:", $rsa->decrypt($resp);







Appendix 2 : Error Code
~~~~~~~~~~~~~~~~~~~~~~~~
======  ==================================================================
code	msg
0	    成功
100001	系统错误
100004	请求参数不合法
100005	签名校验失败
100007	非法IP
100015	商户ID无效
100016	商户信息过期
110004	用户被冻结不可提现
110023	手机号已注册
110055	提现地址错误
110065	请求用户用户不存在（获取用户余额、提现或转账时用到）
110078	提现或转账金额小于最小转出金额（后台配置最小金额，暂时不支持）
110087	提现或转账金额大于最大转出金额（后台配置最大金额，暂时不支持）
110088	请勿重复提交请求
110089	注册手机号不正确
110101	用户注册失败
120202	币种不支持
120402	提现或转账余额不足
120403	提现手续费余额不足
120404	提现或转账金额太小, 小于等于手续费
======  ==================================================================
