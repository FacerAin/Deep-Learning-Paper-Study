> 논문을 읽고 배운 내용을 정리한 글입니다. 잘못된 내용이나 설명이 있을 수 있습니다.

## Title

Graph Convolutional Encoders for Syntax-aware Neural Machine Translation

## Year

2017

## Authors

Jasmijn Bastings, Ivan Titov, Wilker Aziz, Diego Marcheggiani, Khalil Sima’an

## Abstract

기계 번역을 위한 뉴럴 어텐션 기반 인코더 - 디코더 모델에 **Syntatic structure를 통합** 한 효과적이고 간단한 접근법을 소개한다.
**Graph-convolutional networks(GCNs, 그래프 합성곱 신경망)** 에 기반한다.

> GCNs에 대한 설명이 담긴 [링크](https://untitledtblog.tistory.com/152)입니다. GCNs는 기존 이미지를 위한 CNN을 Graph Data에 적용하기 위한 네트워크입니다.

## Introduction

Sequential encoder-decoders 모델은 NMT에서 State-of-the-art 성능을 보였으나, 문법 또는 언어의 계층 구조의 복잡한 모델링에 문제가 있었다.  
 그 이유 중 하나로 Syntactic information(구문 정보)를 NMT에서 효과적으로 다루지 못했기 때문이다.

기존 연구들에서 간접적인 방법으로 구문 정보를 NMT 모델에 통합하거나(eg.Multi-task learning) Syntax 와 Translation task 사이의 인터페이스를 모델링하는데 제한적일 수 있었다.(eg. learning representations of linguistic phrases)

연구의 목표는 인코더에게 _풍푸한 구문 정보(Syntatic information)을 접근_ 할 수 있도록 제공하지만, \*Syntax와 Translation task 사이 상호작용에 제약을 두지 않고, MT가 구문의 어떤 측면이이 이로운지 결정\* 하게 하는 것이다.

엄격한 구문적 제약은 MT를 해를 끼친다는 주장(Andreas Zollmann and Ashish Venugopal. 2006.)과 일치하며, 위 연구는 전통적인 MT에서 이루어졌지만, NMT 방식에도 적용된다고 생각한다.

TBA
