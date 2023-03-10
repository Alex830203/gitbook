# 签名测试

{% tabs %}
{% tab title="C#" %}
{% code overflow="wrap" lineNumbers="true" %}
```csharp
//private Key encrypt
public static string SignAndHash(string dataToSign ,string privatekey)
{
UnicodeEncoding ByteConverter = new UnicodeEncoding();
RSACryptoServiceProvider RSAProvider = new RSACryptoServiceProvider();
var encoder = new UTF8Encoding();
byte[] plaintext = encoder.GetBytes(dataToSign);
RSAProvider.FromXmlString(privatekey);
RSAParameters priKey = RSAProvider.ExportParameters(true);
RSAProvider.ImportParameters(priKey);
byte[] sign = RSAProvider.SignData(plaintext, CryptoConfig.MapNameToOID("MD5"));
return Convert.ToBase64String(sign);
}
//public Key verify
public static bool VerifySignedHash(string dataToSign, string SignedData, string public_key) {
try{
UnicodeEncoding ByteConverter = new UnicodeEncoding();
var encoder = new UTF8Encoding();
RSACryptoServiceProvider RSAalg = new RSACryptoServiceProvider();
RSAParameters priKey = RSAalg.ExportParameters(true);
RSAalg.ImportParameters(priKey);
RSAalg.FromXmlString(public_key);
byte[] plaintext = encoder.GetBytes(dataToSign);
return RSAalg.VerifyData(plaintext, CryptoConfig.MapNameToOID("MD5"),
Convert.FromBase64String(SignedData));
}catch (CryptographicException e){ Console.WriteLine(e.Message + "
Error!!!");
Console.ReadLine();
return false;}}
```
{% endcode %}
{% endtab %}

{% tab title="JAVA" %}
{% code overflow="wrap" lineNumbers="true" %}
```java
// private Key encrypt
public static String sign(byte[] data,String privateKey)throws NoSuchAlgorithmException,
InvalidKeySpecException, InvalidKeyException, SignatureException
{byte[] keyBytes = Base64.getDecoder().decode(privateKey.getBytes());
PKCS8EncodedKeySpec pkcs8EncodedKeySpec = new PKCS8EncodedKeySpec(keyBytes);
KeyFactory keyFactory = KeyFactory.getInstance("RSA");
PrivateKey priKey = keyFactory.generatePrivate(pkcs8EncodedKeySpec);
Signature signature = Signature.getInstance("MD5withRSA");
signature.initSign(priKey);
signature.update(data);
return new String(Base64.getEncoder().encode(signature.sign())); }
//public Key verify
public static boolean verify(byte[] data,String publicKey,String sign)throws Exception{
byte[] keyBytes = Base64.getDecoder().decode(publicKey.getBytes());
X509EncodedKeySpec x509EncodedKeySpec = new X509EncodedKeySpec(keyBytes);
KeyFactory keyFactory = KeyFactory.getInstance("RSA");
PublicKey publicKey2 = keyFactory.generatePublic(x509EncodedKeySpec);
Signature signature = Signature.getInstance("MD5withRSA");
signature.initVerify(publicKey2);
signature.update(data);
return signature.verify(Base64.getDecoder().decode(sign));
}
```
{% endcode %}
{% endtab %}

{% tab title="PHP" %}
{% code overflow="wrap" lineNumbers="true" %}
```php
//RSA PHP URL：https://github.com/phpseclib/phpseclib/tree/1.0
// private Key encrypt
$rsa = new Crypt_RSA();
$rsa→loadKey(xxx）;//xxx private key
$rsa→setSignatureMode(CRYPT_RSA_SIGNATURE_PKCS1);
$rsa→setHash("md5");
$signature = $rsa→sign($plaintext);
echo base64_encode($signature);
// public Key verify
$rsa = new Crypt_RSA();
$rsa->loadKey('publickey');
$rsa→setSignatureMode(CRYPT_RSA_SIGNATURE_PKCS1);
$rsa→setHash("md5");
echo $rsa->verify($plaintext, base64_decode($signature)) ? 'verified' : 'unverified';
```
{% endcode %}
{% endtab %}

{% tab title="NodeJS" %}
{% code overflow="wrap" lineNumbers="true" %}
```javascript
// private Key encrypt
const crypto = require('crypto');
function sign( privateKey, validStr ) {
let signer = crypto.createSign('md5');
signer.update(validStr);
return signer.sign(privateKey, 'base64');
}
// public Key verify
const crypto = require('crypto');
function verify( publicKey, validStr, signature){
let verify = crypto.createVerify('md5');
verify.update(validStr);
return verify.verify(publicKey, signature, 'base64');
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

