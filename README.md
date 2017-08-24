# pe
Pipe Encryptor - A simple tool to encrypt and optionally compress a stream.

## Requirements

* Bash
* OpenSSL
* cat
* lz4 (optional)

## Generating RSA keys
Generate an RSA keypair like so:

`openssl genrsa -out private.pem 4096`

Then extract the public key like so:

`openssl rsa -in private.pem -outform PEM -pubout -out public.pem`

## Encrypting

Simply pipe data in, specifying the public key:

`cat myfile.tar.gz | pe -k /path/to/public.key > myfile.tar.gz.enc`

## Decrypting

Decryption works the same as encryption, just specify the -d switch,
and the private key:

`cat myfile.tar.gz.enc | pe -dk /path/to/private.key > myfile.tar.gz`

## LZ4 Compression

Compression is optional, by specifying the -c option during encryption.

Compression is automatically detected during decryption. 
