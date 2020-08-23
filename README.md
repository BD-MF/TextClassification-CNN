# TextClassification-CNN
The implement of the paper  CNN《Convolutional Neural Networks for Sentence Classification》 based on TF Keras and pytorch.


论文中是使用的CNN框架来实现对句子的分类，积极或者消极。当然这里我们首先必须对CNN有个大概的了解，可以参考我之前的这篇【Deep learning】卷积神经网络CNN结构。目前主流来看，CNN主要是应用在computer vision领域，并且可以说由于CNN的出现，使得CV的研究与应用都有了质的飞跃。

目前对NLP的研究分析应用最多的就是RNN系列的框架，比如RNN,GRU,LSTM等等，再加上Attention，基本可以认为是NLP的标配套餐了。但是在文本分类问题上，相比于RNN，CNN的构建和训练更为简单和快速，并且效果也不差，所以仍然会有一些研究。

那么，CNN到底是怎么应用到NLP上的呢？

不同于CV输入的图像像素，NLP的输入是一个个句子或者文档。句子或文档在输入时经过embedding（word2vec或者Glove）会被表示成向量矩阵，其中每一行表示一个词语，行的总数是句子的长度，列的总数就是维度。例如一个包含十个词语的句子，使用了100维的embedding，最后我们就有一个输入为10x100的矩阵。

在CV中，filters是以一个patch（任意长度x任意宽度）的形式滑过遍历整个图像，但是在NLP中，filters会覆盖到所有的维度，也就是形状为 [filter_size, embed_size]。更为具体地理解可以看下图，输入为一个7x5的矩阵，filters的高度分别为2,3,4，宽度和输入矩阵一样为5。每个filter对输入矩阵进行卷积操作得到中间特征，然后通过pooling提取最大值，最终得到一个包含6个值的特征向量。

