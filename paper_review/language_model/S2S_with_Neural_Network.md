> 논문을 읽고 배운 내용을 정리한 글입니다. 잘못된 내용이나 설명이 있을 수 있습니다.

## Title

Sequence to Sequence Learning with Neural Networks [Link](https://papers.nips.cc/paper/5346-sequence-to-sequence-learning-with-neural-networks.pdf)

## Year

2014

## Authors

Ilya Sutskever, Oriol Vinyals, and Quoc V. Le

## Abstract

DNN(Deep Neural Network)는 복잡한 학습 과정을 수행하는 강력한 모델이다. 라벨링된 거대한 학습 데이터셋을 잘 처리하는 반면 **Sequence To Sequence 매핑에는 사용할 수 없다.**  
👉 연속된 데이터 학습에 취약한 기존 DNN 모델의 한계

따라서 본 Paper에서는 **End-To-End** 접근 방식을 제안함. 다층 LSTM(Long-Short-Term-Memory)를 사용. Input Sequence를 고정된 차원의 벡터에 매핑한 후 다른 deep LSTM에서 대상 시퀀스를 디코딩한다. WMT-14 데이터셋으로부터 영어-프랑스어 번역 작업을 수행하여 34.8의 BLEU 스코어를 달성했다. 이때 **out-of-vocabulary words** 때문에 점수의 하락이 있었음.
추가로 **길이가 긴 문장을 제외**시켰다. 같은 데이터셋에 대해 pharse-based SMT system은 33.3의 BLEU 스코어를 달성했다.  
👉 LSTM 기반의 S2S 모델을 사용하여 구문 기반 SMT에 비해 성능 향상이 있었다. 하지만 out-of-vocabulary와 Long Sentence는 해결하지 못했다.

When we used the LSTM to rerank the 1000 hypotheses produced by the aforementioned SMT system, its
BLEU score increases to 36.5, which is close to the previous state of the art.  
🤔 to rerank the 1000 hypotheses produced by the aforementioned SMT system의 뜻이 무엇인지 잘 모르겠다.

LSTM 모델은 단어 순서에 민감하고 active and the passive voice(?)에 상대적으로 불변하는 감각적인 구절과 문장 표현을 배웠다.

마지막으로, Source Sentence의 단어 순서를 거꾸로했을 때 LSTM의 성능을 현저히 향상되는 것을 발견했다. 그 이유는 source와 target 사이의 많은 단기 의존성(short term dependencies)을 발생시켜 최적화 문제를 더 쉽게 만들었기 때문이다.  
👉 단순하게 Source 시퀀스의 순서를 거꾸로 하는 것만으로도 Short term dependencies의 증가로 성능을 향상시킬 수 있다. 하지만 오히려 과적합(Overfitting) 문제가 있지 않을까?
