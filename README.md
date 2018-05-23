# cidaas-sdk.js
Javascript SDK for Cidaas API
## Install

From CDN

```html
<!-- Latest patch release -->
<script src="https://cdn.cidaas.com/js/cidaas-sdk.js"></script>
```

### Intialize

After Inserting **cidaas-sdk.js** creating local file and name it like **index.js**

#### First Create Options

```js
var options = {

}
```

#### Initialize new Variable With Options

```js
var cidaas = new CidaasSDK(options);
```

### Usuage

#### Login With Browser

Type below after Intialize

```js
cidaas.login();
```

The Above Method will redirect to login page

#### Login Call Back

In your **index.html** After Install cidaas-sdk.js then type logincallback() it is compulsory to redirect after login

```html
<script type="javascript">
  logincallback = function() {
    window.location.href = "https://localhost:5000/index.html";
  }
</script>
```

#### Register With Browser

```js
cidaas.register();
```
The Above Method will redirect to register page

#### Register

```js
cidaas.register({ email: "xxx123@xxx.com",  given_name: "XXXXX", family_name: "YYYYY", password: "123456", 
                  password_echo: "123456", provider: "SELF" }, requestId).then(function (resp) {
      console.log(resp);
      // type your code here
});
```

The Above Method will register user with provided information (Native)

#### UserInfo

```js
cidaas.getUserInfo().then(function (user) {
  // type your code here
}); 
```
The Above method will give userinfo in their callback, you can use your logic to use user information

#### Logout

```js
cidaas.logout().then(function () {
  // type your code here
});
```

In logout method you need give redirect url, if not it will automatically redirect to login page

#### Get Request Id

```js
cidaas.getRequestId().then(function (resp) {
  if (resp && resp.success && resp.data) {
    // type your code here
  } else {
    // type your code here
  }
});
```

The Above Method will give requestid based on your options

#### Get Tenant Info

```js
cidaas.getTenantInfo().then(function (resp) {
  console.log(resp);
  // type your code here
});
```

The Above Method will return Tenant Name and Allow With Login types (email, mobile, passwordless)

#### Get Client Info

```js
cidaas.getClientInfo({requestId: requestId}).then(function (resp) {
   console.log(resp);
  // type your code here
});
```
The Above Method will return Client Name, Enabled Login Providers List, logo_uri and policy_uri

#### Get Registration Setup

```js
cidaas.getRegistrationSetup({requestId: requestId,acceptlanguage: "en-US"}).then(function (resp) {
  console.log(resp);
  // type your code here
});
```

**Request**
```json
{
  "req": "",
  "lang": ""
}
```
**Response**
```json
{
  "res": ""
}
```

When you call **getRegistrationSetup()** you need to pass requestId and acceptlanguage then it will return registration setup in their call back.

#### Get Communication Status

```js
cidaas.getCommunicationStatus({sub: "fd2309fa-290c-4d69-b304-eee88562c2c3"}).then(function (resp) {
  console.log(resp);
  // type your code here
});
```

The Above Method will return verified login type details (ex. email: true)

#### Intiate Account Verification

```js
cidaas.initiateAccountVerification({verificationMedium: "email",requestId: "7cbf7ab4-7eb6-43bf-8f84-40e8213040c0",
                                    processingType: "CODE", sub: "fd2309fa-290c-4d69-b304-eee88562c2c3"}).then(function (resp) {
           console.log(resp);
           // type your code here
});
```

This Method will Initiate Authentication and send mail / message to email / mobile based on verificationMedium with Verification Code.

#### Authenticate Account Verification

```js
cidaas.authenticateAccountVerification({accvid: "839cfa0f-f3a3-4c3b-a322-962834a271ba",code: "788194"}).then(function (resp) {
  console.log(resp);
  // type your code here
});
```

In **authenticateAccountVerification()** you need to pass code, you get this code from email / mobile while call initiate AccountVerification() 

#### Initiate Reset Password

```js
cidaas.initiateResetPassword({email: "xxxxxx@xxx.com",processingType: "CODE",requestId: "7cbf7ab4-7eb6-43bf-8f84-40e8213040c0",
                            resetMedium: "email"}).then(function (resp) {
        console.log(resp);
        // type your code here
});
```

This Method will Initiate Reset Password and send mail / message to email / mobile based on resetMedium with verification Code.

#### Handle Reset Password

```js
cidaas.handleResetPassword({code: "774305",resetRequestId: "23759634-362e-4893-b80d-3f8b8f774c41"}).then(function (response) {
  console.log(response);
});
```

In this Method you need to pass code, you get this code from email / mobile while call initiate AccountVerification() 

#### Change Password
