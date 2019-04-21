# Email Spam Filtering
It uses machine learning models to predict whether the email is spam or ligitimate.


The description about the steps to build a spam filter from scratch can be read from my blog:

It is a python implementation using Naive Bayes Classifier and Support Vector Machines from Scikit-learn ML library.

The results has been shown on two publicly open corpus.

1. Ling-spam corpus
2. Euron-spam corpus

Models includes: KNN, SVM(SVC-rbf), DecisionTree, RandomForest, GBDT, Navie Bayes

https://github.com/abhijeet3922/Mail-Spam-Filtering
https://cloud.tencent.com/developer/article/1117854
https://appliedmachinelearning.blog/2017/01/23/email-spam-filter-python-scikit-learn/


We will walk through the following steps to build this application :

1. Preparing the text data.
2. Creating word dictionary.
3. Feature extraction process
4. Training the classifier

Further, we will check the results on test set of the subset created.

## 1. Preparing the text data.

Training data: 720 emails
Test data: 260 emails
divided equally between **spam** and **ham** mails. 
数据集来源于以下论文：
> Androutsopoulos, Ion, et al. "An evaluation of naive bayesian anti-spam filtering." arXiv preprint cs/0006013 (2000).

通过文本清理（text cleaning）工作，我们将document中的一些无用的字符删除。电子邮件可能包含了大量对spam detection无用的字符，如标点符号、停止词、数字等。Ling-spam 语料库中的邮件已经通过以下方式进行了预处理：
a) 移除停止词—像「and」、「the」、「of」之类的停止词在所有的英语句子当中都非常常见，在判定是否为垃圾邮件时没有多少作用，所以这些词已经从电子邮件中删除。
b) 词形还原（lemmatization）—这是将一个单词的不同变化形式分组在一起的过程，以便其可被视为单个项进行分析。例如，「include」、「includes」和「included」将全部用「include」表示。在词形还原中，句子的语境也会得到保留，而词干提取（stemming）则不会。（词干提取是文本挖掘中的另一个术语，其不会考虑句意）。

经过a、b操作的数据集在lemm_stop文件夹中，共10个部分，用于做交叉验证。

我们还需要从邮件文档中删除非文字信息，比如标点符号或者特殊字符。这里，我们先创建数据词典，再删除这样的词。

## 2. Creating word dictionary.
As a first step, we need to create a dictionary of words and their frequency. ling-sapm 数据集中的示例邮件，第一行是邮件主题（Subject），第二行是空白行，第三行是邮件的正文。对于邮件正文创建词及其频率的词典。创建完数据词典后，remove non-words about which we talked in step 1. 按词频从高到低保留前3000个词，Thus，我们构建了一个3000维的数据字典。

## 3. Feature extraction process
为训练集的每一封邮件构建特征，每一封邮件的特征为一个3000维度的 word count vector. 每一个 word count vector 包含该邮件中3000个最常见的词的词频。


over, 打算删库 -。-