# Persian Grapheme To Phoneme With Transformer

Since Grapheme to Phoneme is a sequence to sequence problem we can use transformer model from the famous paper [[Attention is all you need](https://arxiv.org/abs/1706.03762)] to model the problem.

<img src=https://media.arxiv-vanity.com/render-output/6494154/Figures/ModalNet-21.png width="280" height="400" />

masking,padding,data collating functions are based on the pytorch tutorial for Language Translation in this link [[tutorial](https://pytorch.org/tutorials/beginner/translation_transformer.html)]

In this problem,input sequence and output sequence have differnet vocabulary,like language translation problem.


## Model variations
I trained two variation of transformer model. first with 3 encoder layers and 3 decoder layers.I called this PersianG2P-light.

the second variation has 5 encoder layers and 5 decoder layers.I called this PersianG2P-base.

## Dataset
I'm not allowed to share the dataset but if you have a custom dataset the format of the 'data.csv' file should be something like this :
| grapheme   | phoneme          |
|---------  | ------------      |
| سلام       |  salAm           |


## Usage

 


### 1.For Training,Evaluating and Inference :
open 'PersianG2P.ipynb' in google colab or jupyter notebook and run the cells

### 2.Just Inference :
download PersianG2P-base checkpoint form this [[link](https://drive.google.com/file/d/10zLUN9nDnw-x82_b8SpZAR8NZibRs1WK/view?usp=sharing)]

open 'JustInference.ipynb' in google colab or jupyter notebook and run the cells


## Results
Our dataset had 75000 grapheme and phoneme pairs. so I splitted them into 80% train and 20% test.the following results are evaluated with test data.

There are two common evaluation metrics for grapheme to phoneme problem.[[reference](https://github.com/CiscoDevNet/g2p_seq2seq_pytorch)]

PER (Phonetic error rate) : For each word, calculate the percentage of the total number of predicted phonemes that are correct when compared to the gold phonemes. Average this across all words.

WER (Word error rate): For each word, compare the entire sequence of predicted phonemes to the gold phonemes. We calculate the percentage of words whose predicted phonemes are an exact match to the gold phonemes.

both of these evaluations are calculated with "jiwer" library [[jiwer](https://github.com/jitsi/jiwer)]

 
| Model                  |  PER              |       WER        |  
|---------               | ------------      |  ------------    |
| PersianG2P-light       |  6.5 %            |     28.5 %       |
| PersianG2P-base        |  6.19 %           |     26.5 %       |

### Examples
Here are some random examples :

<img src=https://github.com/sajadalipour7/Persian-Grapheme-To-Phoneme-With-Transformer/blob/main/examples.JPG width="350" height="600" />
