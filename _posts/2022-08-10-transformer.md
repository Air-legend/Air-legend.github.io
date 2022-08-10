---
title: Transformer学习
author: bean
date: 2022-08-10 10:42:00 +0800
categories: [Deep Learning]
tags: [Machine Learning]
---
[bilibili 视频学习链接](https://www.bilibili.com/video/BV1Di4y1c7Zm?p=3&vd_source=e4c855fa1208971df0814fc552a7e0f7)

---

# 编码器
位置编码：
> $PE_(pos,2i) = sin(pos/10000^{2i/d_{model}}) $\
> $PE_(pos,2i+1) = cos(pos/10000^{2i/d_{model}})$

借助正余弦公式:
>   $ sin(\alpha+\beta) = sin\alpha cos\beta + cos\alpha sin\beta $\
> $ cos(\alpha+\beta) = cos\alpha cos\beta - sin\alpha sin\beta   $

$\rightarrow$
>$ PE(pos+k,2i) = PE(pos,2i)*PE(k,2i+1) + PE(pos, 2i+1) *PE(k,2i) $ \
>$ PE(pos+k, 2i+1) = PE(pos,2i+1)*PE(k,2i+1) - PE(pos,2i)*PE(k,2i)$

可以看出， 对于 pos+k 的位置向量某一位 2i 或者 2i+1 而言。可以表示为，pos 位置与 k 位置的位置向量的 2i 与 2i+1 维的线性组合，这样的组合意味着位置向量中蕴涵了相对位置信息。 

ps: 但是这种相对位置信息会在注意力机制那里消失。

最后：embedding + pose_embedding 作为编码器的输入

---

# 注意力机制
> 公式：\
> $ Attention(Q,K,V) = softmax(\frac{QK^T}{\sqrt{d_k}})V $

![QKV生成方式](../common/transformer/注意力机制.png)
![QK相似度](../common/transformer/QK相似度.png)
![实际计算](../common/transformer/计算.png)

