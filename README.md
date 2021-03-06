# English to German Machine Translation

## Dataset

We use the Anki deu-eng language dataset from http://www.manythings.org/anki/. This dataset consists of over 200,000 pairs of sentences in English and German. A sample of the data is as follows:

1. Go.	Geh.	CC-BY 2.0 (France) Attribution: tatoeba.org #2877272 (CM) & #8597805 (Roujin)
2. Hi.	Hallo!	CC-BY 2.0 (France) Attribution: tatoeba.org #538123 (CM) & #380701 (cburgmer)
3. Get away!	Hau ab!	CC-BY 2.0 (France) Attribution: tatoeba.org #240634 (CM) & #662285 (stefz)
4. Run!	Lauf!	CC-BY 2.0 (France) Attribution: tatoeba.org #906328 (papabear) & #941078 (Fingerhut)
5. I prayed.	Ich betete.	CC-BY 2.0 (France) Attribution: tatoeba.org #5828637 (CK) & #4781455 (Tamy)

This data obviously needs to be cleaned. After cleaning, the same data is now

1. Go.	Geh.
2. Hi.	Hallo!
3. Get away!	Hau ab!
4. Run!	Lauf!
5. I prayed.	Ich betete.

After this the English and German sentences are separated, tokenized and padded.

The final train, val and test data sizes are as follows:

* Train_size: 108300
* Val_size: 5700
* Test_size: 6000

## Translation Models

Two machine translation models were built:

1. A Recurrent Neural Network model (LSTMs)
2. A Transformer model

### RNN Model

The RNN model architecture used for English to German machine translation is displayed below.


![alt text](https://github.com/NBK-code/MachineTranslation/blob/main/Images_RNN_Transformer_Models/neural_translation_model_and_key.png?raw=true)


To spped up training a pre-trained English word embedding module from TensorFlow Hub was used. The module is available at https://tfhub.dev/google/tf2-preview/nnlm-en-dim128-with-normalization/1.

The final results after long hours of training were a little underwhelming. So a transformer model was attempted for translation.

### Transformer Model

The transformer model architecture used for English to German machine translation is displayed below.

![alt text](https://github.com/NBK-code/MachineTranslation/blob/main/Images_RNN_Transformer_Models/transformer.png?raw=true)

A sample of final model performance on the test data is given below:

| Input English sentence | German translation by our model | Google Translate of the model German translation |
| ---------- | ----------- | ----------- |
| i'll do as you say. | ich werde tun , was du sagst. | i will do what you say. |
| tom lives with his parents. | tom wohnt bei seinen eltern. | tom lives with his parents. |
| i'm responsible for that. | ich bin dafuer verantwortlich. | i am responsible for it. |
| there are too many choices. | es gibt zu viele dass viele zu viele moeglichkeiten. | there are too many that many too many possibilities. |
| i live in this house by myself. | ich wohne selbst in diesem haus. | i live in this house myself. |

Some of the German translation provided by the model differed from what was given in the test data. So Google Translate was used to translate the model output back to English to verify the performance. From the table, it is clear that the model has succesfully learnt English to German translation. 
