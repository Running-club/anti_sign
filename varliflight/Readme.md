# 飞常准加解密以及签名算法
飞常准app相对比较简单，通过静态分析加简单调试CCCript接口就可以得到。但app接口除了签名以外，还做了一层加密数据传输。

## 签名
签名算法使用的是常见的参数拼接，然后md5加盐的方式，盐很好找。

## 加密
加密采用常规AES算法，但有个点要注意的，静态分析得到的密钥是'nyv2r7jbe048snnyr8t5h6m1re9hnu4k'，但后面进行了md5操作得到一个32位的密钥，而AES128采用的密钥是16位的。因此只要截取前16位就对了。有些语言/库会自动截取前16位。
