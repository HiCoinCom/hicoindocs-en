
4 Appendix
==========
Signature Algorithm
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:Step One: After the request parameters are sorted by dictionary, then they are stitched into a string in the form of key1=value1&key2=value2. stringA = [key1=value1&key2=value2...]

**Note**:

- Sort the dictionary from smallest to largest according to the parameter name.
- If the value of the parameter is empty, it does not participate in the signature.
- Parameter names are case sensitive.
- The request parameter 'sign' doesn't need to be spliced to the signature string.

:Step Two: sign = md5(stringA + app_secret), stringA is the signature string in the first step.


Error Code
~~~~~~~~~~~~~~~~~~~~~~~~
======  ==================================================================
code	msg
0	    Success
100001	system error
100004  request parameter is invalid
100005	signature verification failed
100007	illegal IP
100015	invalid CompanyID
100016	company information is out of date
110004	user account is frozen and withdrawal fails
110023	phone number is registered
110055	withdrawal address error
110065	not exist this user
110078	withdrawal or transfer amount is less than the minimum amount（not support）
110087	withdrawal or transfer amount is greater than the maximum transfer amount（not support）
110088	please do not submit the same API request repeatedly
110089	phone number is incorrect
110101	registration failed
120202	not support this symbol
120402	insufficient withdrawal or transfer amount
120403	insufficient withdrawal fee
120404	withdrawal or transfer amount is less than or equal to the fee
======  ==================================================================


Example
~~~~~~~~~~~~~~~~~~~~~~~~

4.1 Test Parameters
************************

:app_id: 16a9f17fc2ad61ca4339fdd6a8a37f21
:app_secret: 4dedb14fae76dae682de02e671eac408
:URL: http://awstestopenapi.hicoin.one/api/user/createUser

4.2 Sample Code about Signature in Java
****************************************

::

	package com.chainup.coinxman.test;

	import org.apache.commons.httpclient.HttpClient;
	import org.apache.commons.httpclient.methods.PostMethod;
	import org.apache.commons.io.IOUtils;

	import java.io.InputStream;
	import java.io.UnsupportedEncodingException;
	import java.security.MessageDigest;
	import java.security.NoSuchAlgorithmException;
	import java.util.Map;
	import java.util.Set;
	import java.util.TreeMap;

	public class SignTest {

	    /**
	     * main function
	     */
	    public static void main(String[] args) {
	        /** api_key,secret_key */
	        String appId = "16a9f17fc2ad61ca4339fdd6a8a37f21";
	        String appSecret = "4dedb14fae76dae682de02e671eac408";
	        String country = "86";
	        String mobile= "15004648456";
	        String time = "1551325752";

	        /** package parameters */
	        TreeMap<String, String> params = new TreeMap<>();
	        params.put("app_id", appId);
	        params.put("country", country);
	        params.put("mobile", mobile);
	        params.put("time", time);

	        String sign = openApiSign(params, appSecret);
	        params.put("sign", sign);

	        /** http request */
	        String resultJson = post("http://awstestopenapi.hicoin.one/api/user/createUser", params);
	        System.out.println(resultJson);
	    }

	    /**
	     * Signature Algorithm
	     * @param params
	     * @param appSecret
	     * @return
	     */
	    public static String openApiSign(TreeMap<String, String> params, String appSecret){
	        StringBuilder result = new StringBuilder();
	        Set<Map.Entry<String, String>> entrys = params.entrySet();
	        for (Map.Entry<String, String> param : entrys) {
	            /** remove 'sign' param */
	            if(param.getKey().equals("sign")){
	                continue;
	            }

	            /** remove empty string */
	            if(param.getValue()!=null) {
	                result.append("&").append(param.getKey()).append("=").append(param.getValue().toString());
	            }
	        }
	        result.append(appSecret);
	        String signTemp = result.toString().replaceFirst("&","");
	        return getMD5(signTemp);
	    }
	    /**
	     * post request
	     * @param url
	     * @param params
	     * @return
	     */
	    public static String post(String url, Map<String, String> params) {
	        System.out.println(params);
	        String str = null;
	        try {
	            HttpClient client = new HttpClient();
	            PostMethod method = new PostMethod(url);
	            method.setRequestHeader("Content-Type", "application/x-www-form-urlencoded;charset=utf-8");
	            if (params != null && params.size() > 0) {
	                for (Map.Entry<String, String> entry : params.entrySet()) {
	                    method.setParameter(entry.getKey(), entry.getValue());
	                }
	            }
	            int code = client.executeMethod(method);
	            if (code >= 200 && code < 300) {
	                InputStream in = method.getResponseBodyAsStream();
	                str = IOUtils.toString(in);
	            }
	        } catch (Exception e) {
	            // TODO Auto-generated catch block
	            e.printStackTrace();
	        }
	        return str;
	    }



	    /**
	     * md5 string
	     *
	     * @param info
	     * @return
	     */
	    public static String getMD5(String info) {
	        try {
	            MessageDigest md5 = MessageDigest.getInstance("MD5");
	            md5.update(info.getBytes("UTF-8"));
	            byte[] md5Array = md5.digest();
	            return bytesToHex(md5Array);
	        } catch (NoSuchAlgorithmException e) {
	            return "";
	        } catch (UnsupportedEncodingException e) {
	            return "";
	        }
	    }

	    private static String bytesToHex(byte[] md5Array) {
	        StringBuilder strBuilder = new StringBuilder();
	        for (int i = 0; i < md5Array.length; i++) {
	            int temp = 0xff & md5Array[i];
	            String hexString = Integer.toHexString(temp);
	            if (hexString.length() == 1) {
	                strBuilder.append("0").append(hexString);
	            } else {
	                strBuilder.append(hexString);
	            }
	        }
	        return strBuilder.toString();
	    }



4.3 Sample Code about Signature in PHP
***********************************************************

::

	/**
	 * Signature Algorithm
	 * @param array $params
	 * @param $secretKey
	 * @return string
	 */
	function openApiSign(array $params, $secretKey){
	    $stringBuffer = array();
	    ksort($params);
	    foreach ($params as $key => $value){
	        $value = trim($value);
	        if($key == "sign"){
	            continue;
	        }
	        if(!empty($value) && $v!=0){
	            $stringBuffer[] = "{$key}={$value}";
	        }
	    }
	    $str = implode("&", $stringBuffer);
	    return md5($str.$secretKey);
	}
