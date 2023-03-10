# 代码范本

## 登入 API 代码样本

{% tabs %}
{% tab title="C#" %}
{% code overflow="wrap" lineNumbers="true" %}
```csharp
（ASP.NET WEB API framework 4.*）-（Referial full source code）
[HttpPost]//to set this API is using POST method
public HttpResponseMessage RegisterOrLogin()//return HTTP Response Stream
Stream stream =
HttpContext.Current.Request.GetBufferedInputStream();//get HTTP input
HTTP input stream StreamReader reader = new StreamReader(stream);//streamReaderread stream
string jsonPost = reader.ReadToEnd(); //read stream
RegisterOrLoginResp resp = new RegisterOrLoginResp(); //build model object
if (jsonPost.Contains("RegisterOrLoginReq"))//if is RegisterOrLoginReq , handle user authentication request //convert string to object
RegisterOrLoginReq req =
JsonConvert.DeserializeObject <RegisterOrLoginReq> (jsonPost);//read object value
if (req.username == xx && req.password == xx) ……….. return Request.CreateResponse(resp);//return POST response (JSON data)
else if (jsonPost.Contains("UserInfo"))//handle user info request
// business logic –recharge and etc
```
{% endcode %}
{% endtab %}

{% tab title="JAVA" %}
{% code overflow="wrap" lineNumbers="true" %}
```java
（JAVA SPRING WEB API 4.*）-（Refer full source code）
@RequestMapping(value="/login", method = RequestMethod.POST)////API using POST method
public ResponseEntity <RegisterOrLoginResp> ValidateLoginInfo
(HttpServletRequest request, HttpServletResponse response) { // user login verify function
InputStream reader = request.getInputStream();//getHTTP input stream
HTTP input stream BufferedReader br =new BufferedReader(new
InputStreamReader(reader));
//usingstream // convert stream to json string
StringBuilder sb= new StringBuilder();
String jsonString = "";
while((jsonString = br.readLine()) != null) {
sb.append(jsonString);
}
ObjectMapper mapper = new ObjectMapper();//convert JSON to object.
RegisterOrLoginReq req = mapper.readValue(jsonString,RegisterOrLoginReq.class); //convert to object.
RegisterOrLoginResp resp = new RegisterOrLoginResp();//build returnrequest object
if （req.getUsername() == xx && req.getPassword() == xx）{...}
resp.setStatus(200);
//Set object parameter values
return new ResponseEntity(resp,HttpStatus.OK);// return POST response
```
{% endcode %}
{% endtab %}

{% tab title="PHP" %}
{% code overflow="wrap" lineNumbers="true" %}
```php
(PHP 5.5.*) -（Refer full source code）
<?php
$post = file_get_contents('php://input'); //get HTTP input stream
if ($_SERVER[“REQUEST_METHOD”] == “POST”) ｛//check isPOST request
$obj = json_decode($post); // JSON decode
$cmd = $obj→{'cmd'};//read value
if($cmd == "RegisterOrLoginReq"){..｝//handle user login request
if($cmd == "UserInfo"){…}
//handle userinfo request
//set the return parameter value
$data = array('cmd' => 'RegisterOrLoginResp','status'=>200);
header('Content-type: application/json');
echo json_encode($data);｝
```
{% endcode %}
{% endtab %}
{% endtabs %}

## 请求服务器资源代码样本

{% tabs %}
{% tab title="C#" %}
{% code overflow="wrap" lineNumbers="true" %}
```csharp
public class UserInfoResp｛public string username { get; set; } ｝//define model
var client = new WebClient();//create webClient object
var parameters = new NameValueCollection();// using NameValueCollection to package parameter value
parameters["username"] ＝“xx” //Set request value
var response = client.UploadValues("request ip ", parameters);//send POST request to API server
var jsonString = Encoding.Default.GetString(response);// read JSON data
UserInfoResp resp = JsonConvert.DeserializeObject<UserInfoResp>(jsonString); //convert json to object
Console.WriteLine(resp.status);//print value
```
{% endcode %}
{% endtab %}

{% tab title="JAVA" %}
{% code overflow="wrap" lineNumbers="true" %}
```java
CloseableHttpClient client = HttpClients.createDefault();//create
HTTP client object HttpPost httpPost = new HttpPost("request ip URL");
//set POST URL address
ArrayList <NameValuePair> params = new ArrayList<NameValuePair>();
//set parameter value
params.add(new BasicNameValuePair("username", “xxx”)); //set parameter value
httpPost.setEntity(new UrlEncodedFormEntity(params)); // url encode
CloseableHttpResponse response = client.execute(httpPost); //executeHTTP POST request
//get the return POST response result
BufferedReader reader = new BufferedReader(newInputStreamReader(response.getEntity().getContent()));
StringBuilder builder = new StringBuilder(); String line = "";
while( (line = reader.readLine()) != null) {
builder.append(line);
}
ObjectMapper mapper = new ObjectMapper();
UserInfoResp resp = mapper.readValue(builder.toString(),UserInfoResp.class);//Convert JSON string to object
System.out.println(resp.getLoginname());//print value
```
{% endcode %}
{% endtab %}

{% tab title="PHP" %}
{% code overflow="wrap" lineNumbers="true" %}
```php
$data = array('username' => xxx, 'channelId'=>'xx','timestamp'=>xxx,'signature'=>xxx);
$options = array(
'http' => array(
'header' => "Content-type: application/x-www-form-urlencoded",
'method' => 'POST',
'content' => http_build_query($data), ), );
$context = stream_context_create($options);//HTTP POST request
$result = file_get_contents($url, false, $context);//read HTTP POST request return
$obj = json_decode($result);
$status = $obj→{'status'}; //get value
```
{% endcode %}
{% endtab %}
{% endtabs %}
