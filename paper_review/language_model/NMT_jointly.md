> 논문을 읽고 배운 내용을 정리한 글입니다. 잘못된 내용이나 설명이 있을 수 있습니다.

## Title  
Neural Machine Translation by Jointly Learning to Align and Translate [Link](https://arxiv.org/abs/1409.0473)  

## Year
2014 - 2016

## Authors  
Dzmitry Bahdanau, Kyunghyun Cho, Yoshua Bengio  

## Abstract

최근 신경망 기계 번역(Neural Machine Translation)은 기계 번역에서 효과적인 방법으로 주목받고 있다.  
👉 Seq2Seq 모델로 대표되는 신경망 기계번역이 대세. 하지만 Long Term Dependency 등의 문제도 존재.

Neural machine translation is a recently proposed approach to machine translation. Unlike the traditional statistical machine translation, the neural machine translation aims at building a single neural network that can be jointly tuned to maximize the translation performance.  

본 연구에서는 고정 길이 벡터(Fixed-length Vector)가 아키텍처 성능 향상에 병목 현상(Bottleneck)이라 추측하고, 모델이 대상 단어 예측과 관련된 소스 문장의 부분을 자동으로 탐색하여 확장할 수 있는 모델을 제안한다.  
👉 Attention 메커니즘의 기본 개념, 대상 단어를 생성할 때 소스 문장을 참고하자! 


In this paper, we conjecture that the use of a fixed-length vector is a bottleneck in improving the performance of this basic encoder–decoder architecture, and propose to extend this by allowing a model to automatically (soft-)search
for parts of a source sentence that are relevant to predicting a target word, without having to form these parts as a hard segment explicitly.  

새로운 접근을 통해 영어-프랑스어 번역 작업을 state-of-art 성능을 달성했다. 또한 qualitative analysis에 의해 모델의 조정은 인간의 직관과 유사함을 발견하였다.  

With this new approach, we achieve a translation performance comparable to the existing state-of-the-art phrase-based system on the task of English-to-French translation. Furthermore, qualitative analysis reveals that the (soft-)alignments found by the model agree well with our intuition.

## Introduction  
Encoder-Decoder 구조의 NMT가 최근 주목받고 있다. 하지만 fixed-length-vector에 소스 문장에 모든 정보를 압축(compress)하다 보니 길이가 긴 문장에 취약하다는 단점이 있다. 

위 문제를 해결하기 위해서 align and translate jointly하게 학습할 수 있는 인코더-디코더 모델의 확장(extension)을 제안한다.

In order to address this issue, we introduce an extension to the encoder–decoder model which learns to align and translate jointly.  

번역된 단어를 생성할 때마다 모델은 **가장 관련성 높은 정보가 집중된 소스 문장의 위치를 검색**한다.  그리고 모델은 소스 문장의 위치와 context vector 기반으로 target word(번역된 단어)를 예측한다. 



Each time the proposed model generates a word in a translation, it (soft-)searches for a set of positions in a source sentence where the most relevant information is concentrated. The model then predicts a target word based on the context vectors associated with these source positions and all the previous generated target words.  

👉 기존의 Fixed-length vector 정보만을 활용하는 방식보다 발전.  
👉 긴 문장에 더욱 잘 대처할 수 있다.  


The most important distinguishing feature of this approach from the basic encoder–decoder is that it does not attempt to encode a whole input sentence into a single fixed-length vector. Instead, it encodes the input sentence into a sequence of vectors and chooses a subset of these vectors adaptively while decoding the translation. This frees a neural translation model from having to squash all the information of a source sentence, regardless of its length, into a fixed-length vector. We show this allows a model to cope better with long sentences.