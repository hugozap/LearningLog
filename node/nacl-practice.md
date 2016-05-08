# Cryptography with Nacl in the browswer

This snippet uses tweetnacl. There's other popular
version that is compiled with emscriptem (nacl-js)

Following script can be compiled with browserify

```javascript
var nacl = require('tweetnacl');
var randombytes = require('randombytes');
console.log(randombytes(10));

var keypair = nacl.box.keyPair();
var mySecretKey = keypair.secretKey;
var theirKeyPair = nacl.box.keyPair();
var theirPublicKey = theirKeyPair.publicKey;
var theirSecretKey = theirKeyPair.secretKey;
var myPublicKey = keypair.publicKey;

var message = `Hi this is my message, I hope
it will be encrypted ok, who knows bladadsfas
fasdfkajsdf asdlfj alsdjflkadfkja;sdjf;lajsdl;f
asdflasdjfja;sdjfl;asj dfalkjdsfl asldjfl;asdjf
asdfjals;dfjl;ajsdfl;j asdfjalsdkjfal;sdkfjasdf
asdflkjads;fkjl;ajsdlfjalsd fasdjfa sdkfj alsdkjf alsdf
asdlfjalsdfjlasdl falksdjf laksdjf lasd`;

var cl = console.log.bind(console);
cl('Generated keypair');

cl(keypair);

cl('Create keypair using existing key');
cl('private key to use:', keypair.secretKey);
cl(nacl.box.keyPair.fromSecretKey(keypair.secretKey));
cl('Encrypting message:', message);
cl('nonceLength: ', nacl.box.nonceLength);
var nonce1 = randombytes(nacl.box.nonceLength);
cl('Using nonce')
cl(nonce1)
cl(nonce1.length);
cl('Encrypted message:');
var encrypted = nacl.box(new Buffer(message), new Buffer(nonce1), theirPublicKey, mySecretKey)

cl(encrypted)
cl('Now we will decrypt')
var decrypted = nacl.box.open(new Buffer(encrypted), new Buffer(nonce1), myPublicKey, theirSecretKey);
cl(new Buffer(decrypted).toString())

cl('Secret key authentication (secret box) ')

encrypted = nacl.secretbox(new Buffer(message), new Buffer(nonce1),mySecretKey)

cl('Encrypted message only using my secret key:')
cl(encrypted);

cl('Unencrypt message')
decrypted = nacl.secretbox.open(encrypted, new Buffer(nonce1), mySecretKey)
cl(new Buffer(decrypted).toString())

cl('Signatures')
var signPair = nacl.sign.keyPair();
cl(signPair);
cl('Sign our message')
var signed = nacl.sign(new Buffer(message), signPair.secretKey);
cl('signed message')
cl(signed)
cl('length:', signed.length)

cl('hashing')
cl('hash de message 512', nacl.hash(message));

```