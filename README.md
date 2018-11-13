# NLP | Sequence to Sequence Networks| Part 1| Processing text data

There are many benefits you can get by understanding NLP, you can make your own model to answer questions and use it in a chat bot, or you can make a translator to translate a text from your language to English language or the opposite, or maybe you make a text summarizer.

In this tutorial series, we will learn how to make a seq2seq network and train it to translate English text to French, or you can use it in another seq2seq purpose.

In this part of the series, we will learn about processing text data to feed it to the seq2seq network.

## Overview :
*I explained the text processing steps in the next pictures :*


So, to represent the word ball :


and, , to represent the sentence hello world! :


I hope that you got some intuition of the steps of processing the text data.

Now we will do some coding using python :

First, lets import numpy :

``import numpy as np
Then, load the text file:


After that, split the samples and get the necessary dictionaries :


Make the needed dictionaries to convert characters to integers and the opposite :


Compute the length of the longest sample and some other variables:


Output :

```
Number of E Samples  	: 160872
Number of D Samples 	: 160872
Number of D Chars  	: 115
Number of E Chars 	: 92
The Longest D Sample has 351 Chars
The Longest E Sample has 286 Chars
E → the input text ( Will be encoded later )
D → the output text ( Will be decoded later )
```


Next, we will One Hot Encode the samples by letters 
ex:

Hi — -> [[0,0,0,…,1,0,0,0],[0,0,0,…,0,1,0,0]] 
where we represent each sample as an array of zeros that has (n) rows and (j) columns
n = Number of Characters in the longest Sample
j = number of chars in our dictionary

We will make three sets of data :
1- Encoder Input Samples ( English sentences )
2- Decoder Input Samples ( French sentences)
3- Target ( French sentences)

Target will be the same data as Decoder Input but it will be one character ahead of it 
Ex : 
Decoder Input = ‘\tHow are yo’
Target = ‘How are you’


[Output]:
Shape of encoder_input_data : (160872, 286, 92) 
Shape of decoder_input_data : (160872, 351, 115) 
Shape of target_data        : (160872, 351, 115)
Now, the data is ready to be used by a seq2seq model.

## What Next:
In the next part [part 2] we will make the model and train it, then use it to translate English text to French.
