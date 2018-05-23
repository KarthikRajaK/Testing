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

#### Login

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

#### Registeration

```js
cidaas.register();
```
The Above Method will redirect to register page

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
