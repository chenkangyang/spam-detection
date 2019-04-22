# Spam Detection via gcForest

It uses machine learning models to predict whether a term is spam. 

---

<!-- 推特Spam用户检测
```
http://homepages.dcc.ufmg.br/~fabricio/spammerscollection.html

@inproceedings{benevenuto@ceas10,

   author = {Fabr\'{\i}cio Benevenuto and Gabriel Magno and Tiago Rodrigues  and Virg\'{\i}lio Almeida},

   title = {Detecting spammers on Twitter},

   booktitle = {Proceedings of the 7th Annual Collaboration, Electronic messaging, Anti-Abuse and Spam Conference (CEAS)},

   year = {2010},

   location = {Redmond, USA}

}
```
 
 CMU-15688-Project: Twitter Spam Classification: http://www.datasciencecourse.org/

https://nbviewer.jupyter.org/github/sathwikcm/CMU-15688-Project/blob/master/Twitter%20Spam%20Classification%20Notebook.ipynb

sms 检测：
https://www.kaggle.com/uciml/sms-spam-collection-dataset/kernels -->

conduct our experiments on

- UCI-youtube
- UCI-sms

## 文本处理方法 [TF-IDF](https://www.cnblogs.com/nxf-rabbit75/p/9353212.html)

TF-IDF（term frequency–inverse document frequency）是一种用于资讯检索与文本挖掘的常用加权技术。TF-IDF是一种统计方法，用以评估一字词对于一个文件集或一个语料库中的其中一份文件的重要程度。字词的重要性随着它在文件中出现的次数成正比增加，但同时会随着它在语料库中出现的频率成反比下降。TF-IDF加权的各种形式常被搜索引擎应用，作为文件与用户查询之间相关程度的度量或评级。除了TF-IDF以外，互联网上的搜索引擎还会使用基于连结分析的评级方法，以确定文件在搜寻结果中出现的顺序。
1. TF
TF: Term Frequency, 用于衡量一个词在一个文件中的出现频率。因为每个文档的长度的差别可以很大，因而一个词在某个文档中出现的次数可能远远大于另一个文档，所以词频通常就是一个词出现的次数除以文档的总长度，相当于是做了一次归一化。
> TF(t) = (词t在文档中出现的总次数) / (文档的词总数).
2. IDF
IDF: 逆向文件频率，用于衡量一个词的重要性。计算词频TF的时候，所有的词语都被当做一样重要的，但是某些词，比如”is”, “of”, “that”很可能出现很多很多次，但是可能根本并不重要，因此我们需要减轻在多个文档中都频繁出现的词的权重。 
> ID(t) = log(总文档数/词t出现的文档数)

> TF-IDF:上面两个乘起来，就是TF-IDF, TF-IDF = TF * IDF