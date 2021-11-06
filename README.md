# imporved_Transformer
记录学习Transformer结构改进的相关方法和学习心得



## 1、位置编码的优化





## 2、计算复杂度的优化

- **Preformer** ：
- **Atrous Self Attention（如何实现？）**：空洞自注意力机制，在计算相关性的时候只计算隔空位置的计算，直接将计算量变为n²/k；（k是超参数）
- **Local Self Attention（如何实现？）**：中文可称之为“局部自注意力”。其实自注意力机制在CV领域统称为“Non Local”，而显然Local Self Attention则要放弃全局关联，重新引入局部关联。具体来说也很简单，就是约束每个元素只与前后k个元素以及自身有关联（k是超参数）
- **稀疏Attention（如何实现？）**：Atrous Self Attention是带有一些洞的，而Local Self Attention正好填补了这些洞，所以一个简单的方式就是将Local Self Attention和Atrous Self Attention交替使用，两者累积起来，理论上也可以学习到全局关联性，也省了显存。但是OpenAI没有这样做，它直接将两个Atrous Self Attention和Local Self Attention合并为一个。从注意力矩阵上看就很容易理解了，就是除了相对距离不超过kk的、相对距离为k,2k,3k,…k,2k,3k,…的注意力都设为0，这样一来Attention就具有“局部紧密相关和远程稀疏相关”的特性。
- 



## 3、应用场景的优化（如修改Mask方法）





## 4、参考文献

1、《Transformers are RNNs:Fast Autoregressive Transformers with Linear Attention》 2020年