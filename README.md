# iota-seed-vault-client

Typescript library of crypto standards. Ready for AOT and treeshaking in combination with Angular and other modern typescript frameworks.

## Node.js (Install)

Requirements:

- Node.js
- npm (Node.js package manager)

```bash
npm install iota-seed-vault-client
```

### Usage

ES6 import for typical API call signing use case:

```javascript
import { AES } from 'iota-seed-vault-client';

const encryptedMessage = AES.encrypt('message', 'test').toString();
```

Modular include:

```javascript
var AES = require("iota-seed-vault-client").AES;
var SHA256 = require("iota-seed-vault-client").SHA256;
...
console.log(SHA256("Message"));
```

Including all libraries, for access to extra methods:

```javascript
var CryptoTS = require("iota-seed-vault-client");
...
console.log(CryptoTS.HmacSHA1("Message", "Key"));
```

## Client (browser)

Requirements:

- Node.js
- Bower (package manager for frontend)

```bash
bower install iota-seed-vault-client
```

### Usage

Modular include:

```javascript
require.config({
    packages: [
        {
            name: 'iota-seed-vault-client',
            location: 'path-to/bower_components/iota-seed-vault-client',
            main: 'index'
        }
    ]
});

require(["iota-seed-vault-client/algo/aes", "iota-seed-vault-client/algo/sha256"], function (AES, SHA256) {
    console.log(SHA256("Message"));
});
```

Including all libraries, for access to extra methods:

```javascript
// Above-mentioned will work or use this simple form
require.config({
    paths: {
        'iota-seed-vault-client': 'path-to/bower_components/iota-seed-vault-client/iota-seed-vault-client'
    }
});

require(["iota-seed-vault-client"], function (CryptoTS) {
    console.log(CryptoTS.MD5("Message"));
});
```

### Usage without RequireJS

```html
<script type="text/javascript" src="path-to/bower_components/iota-seed-vault-client/iota-seed-vault-client.js"></script>
<script type="text/javascript">
    var encrypted = CryptoTS.AES(...);
    var encrypted = CryptoTS.SHA256(...);
</script>
```

### AES Encryption

#### Plain text encryption

```javascript
var CryptoTS = require("iota-seed-vault-client");

// Encrypt
var ciphertext = CryptoTS.AES.encrypt('my message', 'secret key 123');

// Decrypt
var bytes  = CryptoTS.AES.decrypt(ciphertext.toString(), 'secret key 123');
var plaintext = bytes.toString(CryptoTS.enc.Utf8);

console.log(plaintext);
```

#### Object encryption

```javascript
var CryptoTS = require("iota-seed-vault-client");

var data = [{id: 1}, {id: 2}]

// Encrypt
var ciphertext = CryptoTS.AES.encrypt(JSON.stringify(data), 'secret key 123');

// Decrypt
var bytes  = CryptoTS.AES.decrypt(ciphertext.toString(), 'secret key 123');
var decryptedData = JSON.parse(bytes.toString(CryptoTS.enc.Utf8));

console.log(decryptedData);
```

### List of modules


- ```iota-seed-vault-client/core```
- ```iota-seed-vault-client/x64-core```
- ```iota-seed-vault-client/lib-typedarrays```

---

- ```iota-seed-vault-client/md5```
- ```iota-seed-vault-client/sha1```
- ```iota-seed-vault-client/sha256```
- ```iota-seed-vault-client/sha224```
- ```iota-seed-vault-client/sha512```
- ```iota-seed-vault-client/sha384```
- ```iota-seed-vault-client/sha3```
- ```iota-seed-vault-client/ripemd160```

---

- ```iota-seed-vault-client/hmac-md5```
- ```iota-seed-vault-client/hmac-sha1```
- ```iota-seed-vault-client/hmac-sha256```
- ```iota-seed-vault-client/hmac-sha224```
- ```iota-seed-vault-client/hmac-sha512```
- ```iota-seed-vault-client/hmac-sha384```
- ```iota-seed-vault-client/hmac-sha3```
- ```iota-seed-vault-client/hmac-ripemd160```

---

- ```iota-seed-vault-client/pbkdf2```

---

- ```iota-seed-vault-client/aes```
- ```iota-seed-vault-client/tripledes```
- ```iota-seed-vault-client/rc4```
- ```iota-seed-vault-client/rabbit```
- ```iota-seed-vault-client/rabbit-legacy```
- ```iota-seed-vault-client/evpkdf```

---

- ```iota-seed-vault-client/format-openssl```
- ```iota-seed-vault-client/format-hex```

---

- ```iota-seed-vault-client/enc-latin1```
- ```iota-seed-vault-client/enc-utf8```
- ```iota-seed-vault-client/enc-hex```
- ```iota-seed-vault-client/enc-utf16```
- ```iota-seed-vault-client/enc-base64```

---

- ```iota-seed-vault-client/mode-cfb```
- ```iota-seed-vault-client/mode-ctr```
- ```iota-seed-vault-client/mode-ctr-gladman```
- ```iota-seed-vault-client/mode-ofb```
- ```iota-seed-vault-client/mode-ecb```

---

- ```iota-seed-vault-client/pad-pkcs7```
- ```iota-seed-vault-client/pad-ansix923```
- ```iota-seed-vault-client/pad-iso10126```
- ```iota-seed-vault-client/pad-iso97971```
- ```iota-seed-vault-client/pad-zeropadding```
- ```iota-seed-vault-client/pad-nopadding```