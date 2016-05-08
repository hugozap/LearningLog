# Installing Sodium library for use with Node on debian

Doing npm install sodium didn't work, there was problems with dependencies.

## Solution:

- install some c compiler
- clone repository
https://github.com/paixaop/node-sodium.git
- Manually compile the library with:

```bash
./configure
make check
make
```
