> 논문을 읽고 배운 내용을 정리한 글입니다. 잘못된 내용이나 설명이 있을 수 있습니다.
핑퐁 블로그의 [글](https://blog.pingpong.us/transformer-review/)도 참고하여 학습하였습니다.


## Title  
Attention Is All You Need
 [Link](https://arxiv.org/abs/1706.03762)  

## Year
2017

## Authors  
Ashish Vaswani, Noam Shazeer, Niki Parmar, Jakob Uszkoreit, Llion Jones, Aidan N. Gomez, Lukasz Kaiser, Illia Polosukhin

## Abstract
어텐션 메커니즘을 적용한 인코더-디코더 구조가 좋은 성능을 보였다.
The best performing models also connect the encoder and decoder through an attention mechanism.

위 모델에 비해 본 연구에서 개발한 모델은 영어-독일어 번역 작업에서 2BLEU 이상의 성능 향상이 있었다. 

## Introduction  
Encoder-Decoder 구조의 NMT가 최근 주목받고 있다. 하지만 fixed-length-vector에 소스 문장에 모든 정보를 압축(compress)하다 보니 길이가 긴 문장에 취약하다는 단점이 있다. 

위 문제를 해결하기 위해서 align and translate jointly하게 학습할 수 있는 인코더-디코더 모델의 확장(extension)을 제안한다.

In order to address this issue, we introduce an extension to the encoder–decoder model which learns to align and translate jointly.  

번역된 단어를 생성할 때마다 모델은 **가장 관련성 높은 정보가 집중된 소스 문장의 위치를 검색**한다.  그리고 모델은 소스 문장의 위치와 context vector 기반으로 target word(번역된 단어)를 예측한다. 



Each time the proposed model generates a word in a translation, it (soft-)searches for a set of positions in a source sentence where the most relevant information is concentrated. The model then predicts a target word based on the context vectors associated with these source positions and all the previous generated target words.  

👉 기존의 Fixed-length vector 정보만을 활용하는 방식보다 발전.  
👉 긴 문장에 더욱 잘 대처할 수 있다.  


The most important distinguishing feature of this approach from the basic encoder–decoder is that it does not attempt to encode a whole input sentence into a single fixed-length vector. Instead, it encodes the input sentence into a sequence of vectors and chooses a subset of these vectors adaptively while decoding the translation. This frees a neural translation model from having to squash all the information of a source sentence, regardless of its length, into a fixed-length vector. We show this allows a model to cope better with long sentences.