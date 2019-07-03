java 提供的加解密工具类在 java.security和javax.crypto包下


SecureRandom：用于生成随机或伪随机数字。

MessageDigest：用于计算指定数据的消息摘要（散列）。

Signature：使用密钥初始化，这些签名用于签署数据并验证数字签

Cipher：用密钥初始化，用于加密/解密数据。存在各种类型的算法：对称批量加密（例如AES），非对称加密（例如RSA）和基于密码的加密（例如PBE）。

Message Authentication Codes（MAC）：与MessageDigests一样，它们也会生成散列值，但是首先使用密钥初始化以保护消息的完整性。

KeyFactory：用于将Key类型的现有不透明密钥转换为密钥规范（底层密钥材料的透明表示），反之亦然。

SecretKeyFactory：用于将SecretKey类型的现有不透明加密密钥转换为密钥规范（底层密钥材料的透明表示），反之亦然。

SecretKeyFactorys是专门的KeyFactorys，只能创建密钥（对称）。

KeyPairGenerator：用于生成一对适用于指定算法的公钥和私钥。

KeyGenerator：用于生成与指定算法一起使用的新密钥。

KeyAgreement：由两方或多方使用，商定和建立一个特定的密钥，用于特定的密码操作。

AlgorithmParameters：用于存储特定算法的参数，包括参数编码和解码。

AlgorithmParameterGenerator：用于生成适合于指定算法的一组AlgorithmParameters。

KeyStore：用于创建和管理密钥库。密钥库是密钥的数据库。密钥库中的私钥具有与其关联的证书链，用于验证相应的公钥。密钥库还包含来自可信实体的证书。

CertificateFactory：用于创建公钥证书和证书吊销列表（CRL）。

CertPathBuilder：用于构建证书链（也称为证书路径）。

CertPathValidator：用于验证证书链。

CertStore：用于从存储库中检索证书和CRL。