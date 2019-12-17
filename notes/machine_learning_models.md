# machine_learning_models

## word embedding（词嵌入、词向量）

- 一种把词向量化的概念
- 向量化的过程要满足分布表示，即若干元素的连续表示形式
- 并不是一个具体的技术
- 常见word embedding技术：
  - Embedding Layer（基于Word2Vec）
  - GloVe

### 情况一：输入标量（升维）

只把文本的字/词一一映射成标量，还没有把标量映射成向量形式  
结果：输入标量(如：666)，输出向量[0.25,0.22,0.5……]（out_put维），就是升维

### 情况二：直接输入one-hot向量（降维）

![one-hot-to-embedding](https://img-blog.csdnimg.cn/20190412220355799.png)
通过一个字向量表W，和one-hot向量矩阵作运算，达到降维效果

## CNN（卷积神经网络）

- 提取图像的特征
- 局部提取
- 卷积核选取：卷积核大小、卷积核数量……

## Conv1D

- 单轴滑动，故名1D
- 只需指定卷积核的第一维，第二维会自动匹配

## Conv2D

- 双轴滑动，故名2D
- 指定卷积核为一个矩形

## Pooling （池化）

- 通过部分采样达到特征降维
- 特征不变形
- 某种程度上，能避免过拟合
- 有很多池化函数，但一般采用MaxPooling

## MaxPooling1D

- 相当于在第一维降维

## MaxPooling2D

![MaxPooling2D](https://img2018.cnblogs.com/blog/991470/201902/991470-20190208201508704-368644792.png)

- 相当于2个维度同时降维

## Flatten层

- “压平”：多维向量一维化
- 常用于卷积到全连接层的过渡

## RNN：用于更好地处理序列信息

- 当前时刻的隐藏层由输入、上一时刻的隐藏层共同影响
- 可以训练双向RNN增强效果  
![RNN](https://pic3.zhimg.com/80/v2-9e50e23bd3dff0d91b0198d0e6b6429a_hd.jpg)  

## 几种架构

![RNN](https://pic2.zhimg.com/80/v2-6522f0e0cd9740f45e1ee46591898081_hd.jpg)

### 1toN

![itoN](https://pic3.zhimg.com/80/v2-87ebd6a82e32e81657682ffa0ba084ee_hd.jpg)

![1toN](https://pic1.zhimg.com/80/v2-16e626b6e99fb1d23c8a54536f7d28dc_hd.jpg)

应用场景：图片标注（输入图像特征，输出一段描述图片的句子）、音乐生成（输入类别，输出一段music）  

### Nto1

![RNN](https://pic1.zhimg.com/80/v2-6caa75392fe47801e605d5e8f2d3a100_hd.jpg)
应用场景：文本分类

### NtoM（Seq2Seq）

![RNN](https://pic4.zhimg.com/80/v2-77e8a977fc3d43bec8b05633dc52ff9f_hd.jpg)

## 缺点

没有长期记忆功能！

## LSTM（长短期记忆）

- RNN的改良，解决梯度消失和爆炸问题
- 可携带信息跨越多个时间步

## BiLSTM（双向长短期记忆）

## CRF（条件随机场）

- 词性标注

## Dropout

## Transformer

- 抛弃CNN/RNN，均由Attention机制组成
- 通过堆叠Transformer搭建神经网络

----

- Transformer = Encoder + Decoder
- Encoder和Decoder各有6个，编码器的输出会被当做解码器的输入
- 一个Encoder = self-attention + Feed Forward Neural Network
![self-attention](https://www.zhihu.com/equation?tex=%5Ctext%7BAttention%7D%28Q%2CK%2CV%29%3D%5Ctext%7Bsoftmax%7D%28%5Cfrac%7BQK%5ET%7D%7B%5Csqrt%7Bd_k%7D%7D%29V+%5Ctag1)

![FFN](https://www.zhihu.com/equation?tex=%5Ctext%7BFFN%7D%28Z%29+%3D+max%280%2C+ZW_1+%2Bb_1%29W_2+%2B+b_2+%5Ctag2)

- 一个Decoder = self-attention + Encoder-Decoder Attention + Feed Forward Neural Network

----

![self-attention](https://pic1.zhimg.com/80/v2-79b6b3c14439219777144668a008355c_hd.jpg)

- 先使用词嵌入得到1\*512维的Embedding
- Embedding分别乘512\*64的矩阵W_q，W_k，W_v（所有Embedding共享一套参数矩阵）得到1\*64的Q、K、V,代入（1）得到1\*64的加权V向量
- 所有的V向量加起来，得到真正的输出（如图上两个单词Thinking和Machines，两个Score都是用q1向量计算的，这意味着我们是在查询每个单词和Thinking的Attention程度）

## Bert

文本->input_ids(batch_size,word_id，词id表示)->sequence_output(词向量表示)->pooled_output(句向量表示)

## HMM

### 简述

- 概率图模型：用图来表达变量相关关系
  - 贝叶斯网：有向图
  - 马尔科夫网：无向图
- 用贝叶斯网（有向无环图）表示
- 用于时序数据建模
- “HMM模型中有两组变量，观测变量和状态变量，我们认为状态变量是隐藏的不可观测的（故称作隐）
- 观测变量依赖于当前时刻的状态变量，有**输出观测概率矩阵B**
- 状态变量依赖于前一时刻的状态变量，与更之前的状态变量无关（马尔科夫条件），有**状态转移概率矩阵A**
- **初始状态概率π**=(π1,π2,……,πn)，其中πi=P(y1=si)
- **状态的有限集合**，即标注集
- **观测的有限集合**，即文本的词语
