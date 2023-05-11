### DigestAuthMemory
====================

Javascript implementation of 
[RFC 2716 HTTP Digest Authentication](https://datatracker.ietf.org/doc/html/rfc7616) 
with support for MD5, SHA-256, SHA-512-256 and session variant, username hashing, 
stale nonce handler and more.

Forge library from [digitalbazaar/forge](https://github.com/digitalbazaar/forge) is 
required.

### Usage:

#### GET
```js
let url = "./api/get";
let getData = "message=hello!&foo=bar";

let req = new digestAuthRequest('GET', url + "?" +  getData, "username", "password");
req.request(function(resp){
    console.log(resp);
    document.getElementById("outputGet").innerHTML = "GET : "+resp.message;
},function(errorCode){
    console.log("Error " + errorCode);
    document.getElementById("outputGet").innerHTML = "GET : "+errorCode;
});
```

#### POST (send as application/json)
```js
let url = "./api/post";
let postData = {message:'Hello', foo:'bar'};

let req = new digestAuthRequest('POST', url);
req.request(function(resp){
    console.log(resp);
    document.getElementById("outputPost").innerHTML = "POST : "+resp.message;
},function(errorCode){
    document.getElementById("outputPost").innerHTML = "POST : "+errorCode;
    console.log("Error " + errorCode);
},postData);
```

#### POST (send as application/x-www-form-urlencoded)
```js
let url = "./api/post";
let postData = "message=hello!&foo=bar";

let req = new digestAuthRequest('POST', url);
req.request(function(resp){
    console.log(resp);
    document.getElementById("outputPost").innerHTML = "POST : "+resp.message;
},function(errorCode){
    document.getElementById("outputPost").innerHTML = "POST : "+errorCode;
    console.log("Error " + errorCode);
},postData);
```