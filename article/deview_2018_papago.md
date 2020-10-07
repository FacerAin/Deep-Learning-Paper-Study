> Deview 2018 Papago Internals: 모델분석과 응용기술 개발 발표를 정리한 글입니다.[링크](https://deview.kr/2018/schedule/241)  [발표자료 링크](https://www.slideshare.net/deview/245papago-internals-119175259)

### Title
Papago Internals: 모델분석과 응용기술 개발  

### Content
AI 연구 개발 프로세스  
1. 모델 연구/개발
2. 응용 기술 연구/개발
3. 앱/웹 서비스 개발
4. 서버 개발

파파고 팀은 품질과 편의성 최적화에 집중한다.  

### 학습과 수렴 관련 연구

기계 번역 모델은 일반화된 학습과 수렴 기준이 없다. (문제점 1)Tranformer 모델은 수렴 지점 선별 기준을 명시하지 않았고, ConvSeq2Seq 모델은 Learning Rate 기준의 수렴 지점을 선별한다.

일반화된 모델 평가 방법으로 BLEU를 사용하지만, BLEU 점수가 높다고 높은품질을 보장하지는 않는다. (문제점 2)
**전문가 평가 방법**을 사용. 2개 국어에 능통한 전문가가 원문과 번역문의 Adequancy와 Fluency를 기반으로 평가한다.

### 앞의로의 연구 방향
1. 서비스 품질 개선
- 신뢰할 수 있는 모델 학습 및 수렴 지점 탐색 방법
- 장문, 저빈도 단어, 고유명사 번역 품질 개선
2. 서비스 속도 개선
-  번역 품질은 유지하며 Interface 더욱 빠르게
-  Quantization, Model Compression, Lower-bit Calculation

### 인공 신경망을 이용한 웹사이트 번역

목표: 신경망 기반 번역을 통해 번역 품질을 확보 후, 번역문의 적당한 위치에 원문의 태그들을 삽입한다.

[참고 링크](https://www.slideshare.net/deview/245papago-internals-119175259/32)

적당한 위치는 attention 값을 바탕으로 추정.
좋은 성능을 발휘함.  

Practical Issues  
- "지저분"한 웹 상의 문서
- 커다란 HTML 페이지에서 "번역할 부분"만 추출
- 번역문에 원문의 HTML 태그를 "적절한 위치"에 삽입
- 이 모든 과정을 "빠르게 처리"하기  


