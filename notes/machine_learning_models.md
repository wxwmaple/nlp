# word embedding（词嵌入、词向量）
- 一种把词向量化的概念
- 向量化的过程要满足分布表示，即若干元素的连续表示形式
- 并不是一个具体的技术
- 常见word embedding技术：
    - Embedding Layer（基于Word2Vec） 
    - GloVe
## 情况一：输入标量（升维）
只把文本的字/词一一映射成标量，还没有把标量映射成向量形式  
结果：输入标量(如：666)，输出向量[0.25,0.22,0.5……]（out_put维），就是升维     
## 情况二：直接输入one-hot向量（降维）
![one-hot-to-embedding](https://img-blog.csdnimg.cn/20190412220355799.png)
通过一个字向量表W，和one-hot向量矩阵作运算，达到降维效果










# CNN（卷积神经网络）
- 提取图像的特征
- 局部提取
- 卷积核选取：卷积核大小、卷积核数量……
## Conv1D：
- 单轴滑动，故名1D
- 只需指定卷积核的第一维，第二维会自动匹配
## Conv2D：
- 双轴滑动，故名2D
- 指定卷积核为一个矩形





# Pooling （池化）
- 通过部分采样达到特征降维
- 特征不变形
- 某种程度上，能避免过拟合
- 有很多池化函数，但一般采用MaxPooling
## MaxPooling1D：
- 相当于在第一维降维
## MaxPooling2D：
![MaxPooling2D](https://img2018.cnblogs.com/blog/991470/201902/991470-20190208201508704-368644792.png)
- 相当于2个维度同时降维





# Flatten层
- “压平”：多维向量一维化
- 常用于卷积到全连接层的过渡








# RNN：用于更好地处理序列信息
- 当前时刻的隐藏层由输入、上一时刻的隐藏层共同影响
- 可以训练双向RNN增强效果  
![RNN](https://pic3.zhimg.com/80/v2-9e50e23bd3dff0d91b0198d0e6b6429a_hd.jpg)  

## 几种架构
![RNN](https://pic2.zhimg.com/80/v2-6522f0e0cd9740f45e1ee46591898081_hd.jpg)
### 1toN
![](https://pic3.zhimg.com/80/v2-87ebd6a82e32e81657682ffa0ba084ee_hd.jpg)
![](https://pic1.zhimg.com/80/v2-16e626b6e99fb1d23c8a54536f7d28dc_hd.jpg)
应用场景：图片标注（输入图像特征，输出一段描述图片的句子）、音乐生成（输入类别，输出一段music）  

### Nto1
![RNN](https://pic1.zhimg.com/80/v2-6caa75392fe47801e605d5e8f2d3a100_hd.jpg)
应用场景：文本分类
### NtoM（Seq2Seq）
![RNN](https://pic4.zhimg.com/80/v2-77e8a977fc3d43bec8b05633dc52ff9f_hd.jpg)

## 缺点
没有长期记忆功能！

# LSTM（长短期记忆）
- RNN的改良，解决梯度消失和爆炸问题
- 可携带信息跨越多个时间步

# BiLSTM（双向长短期记忆）


# CRF（条件随机场）
- 词性标注

# Dropout
