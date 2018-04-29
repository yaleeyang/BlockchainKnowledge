# GeoHash和Crypto-Spatial Coordinates（CSC）

## GeoHash
GeoHash算法将经纬度二维数据编码为一个字符串，本质上是一个二维变一维，一个降维的过程。
![GeoHash Fig1](https://raw.githubusercontent.com/yaleeyang/BlockchainKnowledge/master/images/GeoHash.jpg)

如左图所示，空间分为四块时，从左下，左上，右下，右上，编码顺序依次为00, 01, 10, 11的Z形曲线；当我们将各块分解为四个子块，共16个块时，编码顺序如右图所示。大块与大块之间也遵循Z行曲线原则，这种类型的曲线被称为Peano空间填充曲线，编码方式为四叉树线性编码方式。对经纬度合并后的编码，进行base32编码，最后形成GeoHash编码。例如，故宫（116.40382,39.918118）的GeoHash编码为wx4g0ffe。

GeoHash的优点是，对大部分编码而言，相似的编码距离也相近，缺点是有些临近编码具有空间突变性，比如右图的0111到1000，空间距离差距很大。

## Crypto-Spatial Coordinates（CSC）
CSC是Foam.Space提出的一种基于GeoHash的加密的时空坐标，其核心是结合智能合约地址，让基于位置的智能合约的运行发生在指定的真实世界位置上。如下图所示，我们看看，它如何生成出来？
![CSC Fig1](https://raw.githubusercontent.com/yaleeyang/BlockchainKnowledge/master/images/Crypto-Spatial-Coordinates.png =680x)

GeoHash地址和以太坊地址拼接后再用base58编码即为CSC编码地址，这种编码方式也是比特币钱包地址编码方式。CSC提供了一种结合位置和智能合约的编码模式，可以在1平方米的区域，绑定任意多的智能合约，从而将智能合约关联到物理空间。当然编码方式只是提供一种手段，真正的目的是提供唯一索引，还是在为PoL铺桥搭路。