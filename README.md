# Machine Translation

We perform machine translation from English to German using two models:
1. A Recurrent Neural Network model (LSTMs)
2. A Transformer model

We use the Anki deu-eng language dataset from http://www.manythings.org/anki/ to train and test the model. This dataset consists of over 200,000 pairs of sentences in English and German. But we will work with only a subset of the data to reduce training time. Both the RNN and the Transformer models are trained with appropriate metrics and finally the inference is done using the test data.
