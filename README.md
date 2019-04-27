# Spam Detection via deep forest

It uses machine learning models to predict whether a term is spam. 

The experiments are performed on the following two data sets

- UCI-youtube
- UCI-sms

The text processing methods including:
- Remove the stop words
- Build word count vector
- TF-IDF
- Texts to sequences



Examples of Texts to sequences approach：
```python
from keras.preprocessing.text import Tokenizer
text1='Some ThING to eat !'
text2='some thing to drink .'
texts=[text1,text2]
print(texts)
#out:['Some ThING to eat !', 'some thing to drink .']
tokenizer = Tokenizer(num_words=100) #num_words:None或整数,处理的最大单词数量。少于此数的单词丢掉
tokenizer.fit_on_texts(texts)
print( tokenizer.word_counts) 
#out:OrderedDict([('some', 2), ('thing', 2), ('to', 2), ('eat', 1), ('drink', 1)])
print( tokenizer.word_index) 
#out:{'some': 1, 'thing': 2, 'to': 3, 'eat': 4, 'drink': 5}
sequences = tokenizer.texts_to_sequences(texts)
word_index = tokenizer.word_index
print(sequences)
#out:[[1, 2, 3, 4], [1, 2, 3, 5]] 转换为序列，注意这里句子等长，所以输出一样，但是不等长句子输出的长度是不一样的
print('Found %s unique tokens.' % len(word_index))
#out:Found 5 unique tokens.
SEQ_LEN = 10
data = pad_sequences(sequences, maxlen=SEQ_LEN)
print(data)
#out:[[0 0 0 0 0 0 1 2 3 4]
# [0 0 0 0 0 0 1 2 3 5]]
```