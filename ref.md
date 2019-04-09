# 非對稱加密 in openssl

1. 產生 CA 的 certificate 和 private key
2. 產生 server 的 certificate sign request (CSR) 和 private key
3. 產生 client 的 certificate sign request (CSR) 和 private key
4. 用 CA 簽署 server 和 client 的 CSR，輸出 certificate（即包含 public key）

## 手把手教學

1. [概念解說](https://gist.github.com/Soarez/9688998)
2. [程式步驟](https://stackoverflow.com/questions/21297139/how-do-you-sign-a-certificate-signing-request-with-your-certification-authority/21340898#21340898)
3. [常用 functions](https://stackoverflow.com/questions/21050366/testing-ssl-tls-client-authentication-with-openssl)