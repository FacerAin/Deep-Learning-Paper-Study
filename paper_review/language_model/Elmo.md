> 논문을 읽고 배운 내용을 정리한 글입니다. 잘못된 내용이나 설명이 있을 수 있습니다.

## Title

Deep contextualized word representations

## Year

2018

## Authors

Matthew E. Peters, Mark Neumann, Mohit Iyyer, Matt Gardner, Christopher Clark, Kenton Lee, Luke Zettlemoyer

## Abstract

본 논문에서는 아래를 모두 모델링할 수 있는
deep contextualized word representation 모델을 제안함.

- 단어 사용의 복잡한 특징 (구문 및 의미론)
- 이것들이 언어적 맥락에 따라 어떻게 다르게 사용되는지

Word Vector는 양방향 언어 모델(biLM)의 내부 state의 함수로부터 학습한다.
이 representation은 존재하는 모델에 쉽게 추가할 수 있고, 6개의 도전적인 NLP 문제들(question answering, textual entailment and sentiment analysis 등) 성능을 크게 향상 시킨다.  
👉 기존의 단어 단위 임베딩 방식 (Word2Vec, Glove 등)은 다의어를 제대로 반영하지 못하는 문제가 있었다. 하지만 본 모델은 구문 및 의미론 즉, 다의어를 반영할 수 있다.

We also present an analysis showing that exposing the deep internals of the pre-trained network is crucial, allowing downstream models to mix different types of semi-supervision signals.  
🤔 downstream model과 semi-supervision signals의 의미를 잘 모르겠다.

## Introduction

Pre-trained 된 Word Representation은 NLP 모델의 중요한 부분이었다. 그러나 높은 품질의 word representation은 어려운 문제였다.

- 단어 사용의 복잡한 특징 (구문 및 의미론)
- 이것들이 언어적 맥락에 따라 어떻게 다르게 사용되는지

따라서 본 논문에서는 위 두 문제를 해결하고, 이미 존재하는 모델에 쉽게 결합할 수 있고, 자연어 이해 문제에서 좋은 성능을 낼 수 있는 새로운 모델을 제안한다.

본 방식은 전통적인 단어 단위 임베딩과 차이가 있는데, 각 token은 전체 입력 문장(Input Sequence)의 함수인 Representation으로 할당된다. 큰 text Corpus 바탕의 결합된 LM objective로 훈련된 양방향 LSTM으로부터 파생된 Vector를 사용한다. 이와 같은 이유로 이것을 **ELMo**(**E**mbedding from **L**anguage **Mo**dels)라 부른다.

이전의 접근과 다르게, ELMo representation은 biLM의 모든 내부 층에서 함수라는 의미에서 deep하다.
좀 더 자세히 말하면, 각 end task에 대해 각 입력 단어 위에 쌓인 벡터들의 **선형 조합(Linear Combination)**을 학습한다. 이는 최상위 LSTM 계층만을 사용하는 것에 비해 성능이 현저히 향상된다.

이러한 방식으로 내부 state를 결합하면 매우 풍부한 단어 representation이 가능하다.

본질적인 평가를 사용하여, 높은 level의 LSTM state는 단어 의미의 문법 의존적인 측면을 감지하고, 낮은 level의 LSTM state는 구문 측면을 감지한다.
🤔 LSTM에서 state의 높고 낮음은 어떻게 결정하는 것일까?

동시에 모든 신호를 노출하는 것은 유용하며, 학습된 모델들이 각 end task에 가장 유용한 semi-supervision의 유형을 선택할 수 있다.
🤔 위에서도 언급했듯이, semi-supervision이 무엇일까?
