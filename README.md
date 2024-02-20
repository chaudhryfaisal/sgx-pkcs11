# PKCS#11 implementation in Intel SGX enclaves
## Build
1. Install the [SGX driver](https://github.com/intel/linux-sgx-driver);
2. Install the [SGX SDK and SGX PSW](https://github.com/intel/linux-sgx):
    * when you'll be asked where to install SGX SDK, enter `/opt/intel`;
3. Compile SGX SSL Library:
   * Download [openssl-3.0.10*.tar.gz](https://www.openssl.org/source/openssl-3.0.10.tar.gz).
   * Download [intel-sgx-ssl 3.0_Rev1 branch](https://github.com/intel/intel-sgx-ssl).
   * Move `openssl-*.tar.gz` into `intel-sgx-ssl/openssl_source`
   * Compile intel-sgx-ssl:
        ```
        cd intel-sgx-ssl/Linux
        make all test SGX_MODE=SIM
        sudo make install
        ```
4.  Clone this project.
5.  Compile this project:
    ```
    cd SGX-PKCS11
    make SGX_MODE=SIM
    ```
6.  Test:
    ```
    ./App Makefile
    
      PKCS11 interface Initialization done
      PKCS11 session opened and Intel SGX initialized
      
      Intel SGX created and returned a pair of RSA keys:
      1-clear RSA public key
      2-private RSA key encrypted with AES-256-cbc
      
      Message to encrypt:
      all:
      
      Encryption initialization...
      Intel SGX has encrypted the message by using the public RSA key
      
      Decryption initialization...
      Intel SGX has decrypted the message by using the private encrypted RSA key
      Decrypted message:
      all:
      
      PKCS11 session closed and Intel SGX closed
      PKCS11 interface closed
      Exit...    
    ```
    
