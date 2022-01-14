# 예술의전당 고객 특성분석 - 회원, 공연 데이터를 중심으로

## 📃 개요
### 예술의전당 고객관계관리(CRM)을 위한 빅데이터 기반 고객 특성 파악 및 문화예술공연 기획, 운영, 마케팅 전략 제시

## 📃 주요 분석
* 고객 기초통계 분석
* 군집화 및 군집특성 분석
* 장르구매패턴분석
* [기계학습을 활용한 구매예측모형](https://github.com/chIorophyII/ArtCenter_Project/tree/main/Code/%EA%B8%B0%EA%B3%84%ED%95%99%EC%8A%B5%EC%9D%84%ED%99%9C%EC%9A%A9%ED%95%9C%EA%B5%AC%EB%A7%A4%EC%98%88%EC%B8%A1%EB%AA%A8%ED%98%95)

## 📃 프로세스
### (1) 데이터셋 설정
- 활용 데이터 및 용어 정의
- 각 분석별 목적에 맞는 데이터셋 정제 및 전처리

### (2) 분석 과정
1. 고객 기초통계 분석  
```
- 인구통계학적 특성(성별, 연령, 거주지역)
- 회원등급별 특성(무료회원, 유료회원)
- 거래 및 활동 특성(결제건수, 회당평균결제금액, 회당평균구매티켓수, 최근구매후경과일, 아카데미수강유무)
- 구매공연 특성(구매장르수비중, 구매공연중 개별장르비중)
```

2. 고객군집화 및 군집특성 분석
```
- 군집화의 기준이 되는 변수는 CRM에서 많이 사용되는 개념 중 하나인 RFM을 사용
  Recency(최근성) : 마지막 구매 후 지난 기간(일)
  Frequency(구매빈도) : 최근 3년 동안의 결제건수 합계
  Monetary(구매금액) : 최근 3년 동안의 1회 결제 시 평균 결제금액
- K-maans 알고리즘을 사용해 군집개수 결정 및 군집 특성 파악
```

3. 장르 구매패턴 분석
```
- 각 장르별 '구매티켓수'와 '공연관람횟수'에 대한 연관규칙분석을 통해 장르 구매패턴 도출
- 장르 중복구매 고려 여부에 따라 분석
- 평가지표 : 지지도(Support), 신뢰도(Confidence), 향상도(Lift)
```

4. [기계학습을 활용한 구매예측모형](https://github.com/chIorophyII/ArtCenter_Project/blob/main/Code/%EA%B8%B0%EA%B3%84%ED%95%99%EC%8A%B5%EC%9D%84%ED%99%9C%EC%9A%A9%ED%95%9C%EA%B5%AC%EB%A7%A4%EC%98%88%EC%B8%A1%EB%AA%A8%ED%98%95/Purchase_Prediction_Model.ipynb)
```
- 재구매에 영향을 미칠 것이라고 예상되는 변수들을 선정하고 재구매 여부 예측 모델을 개발 및 재구매에 영향을 미치는 주요 변수 탐색
- 예측 기법으로 의사결정나무(Decision Tree), 랜덤 포레스트(Random Forest), XGBoost 활용 후 Voting Classifier를 사용해 최종 모델 결정
- 성능 측정 지표 : ROC AUC Score, Accuracy Score, Recall
```
## [결과 자료](https://github.com/chIorophyII/ArtCenter_Project/blob/main/Result/%EC%98%88%EC%88%A0%EC%9D%98%EC%A0%84%EB%8B%B9_%EA%B2%B0%EA%B3%BC%EC%9E%90%EB%A3%8C.pdf)

## 기타
[예술의전당 감사 공문 수신](https://github.com/chIorophyII/ArtCenter_Project/blob/main/Result/%EC%98%88%EC%88%A0%EC%9D%98%EC%A0%84%EB%8B%B9_%EA%B0%90%EC%82%AC%EA%B3%B5%EB%AC%B8.png)
  
