# 기계학습을 활용한 구매예측모형
## 1. 구매예측모형 과정
- 본 분석에서는 예술의전당 상품 구매에 대한 회원 데이터를 사용해 재구매에 영향을 미칠 것이라고 예상되는 변수들을 선정, **고객의 재구매 여부를 예측할 수 있는 모델을 개발**하고, **재구매에 큰 영향을 미치는 주요 변수를 찾는 것**을 목적으로 함
- 분석대상은 **2018년 7월부터 2021년 6월까지 3년 간 예술의전당을 한 번이라도 이용한 전체 고객(74,204명)을 대상**으로 하며, **종속변수**는 다른 날짜 또는 다른 공연을 재결제한 경우(2회 이상 결제)와 그렇지 않은 경우를 구분하는 범주형(이분형, 1 또는 0의 값)변수임
- 전체 74,204명 중 랜덤추출을 통해 70%의 데이터(Training Data Set)는 예측 모형 훈련에 사용, 나머디 30% 데이터(Test Data Set)는 결과값이 없는 데이터라고 간주. Training Data Set을 이용해 생성된 예측모형이 새로운 데이터에서도 잘 작동할지(예측력)를 평가함

### 구매예측모형 투입 변수
![변수](https://github.com/chIorophyII/ArtCenter_Project/blob/main/Code/%EA%B8%B0%EA%B3%84%ED%95%99%EC%8A%B5%EC%9D%84%ED%99%9C%EC%9A%A9%ED%95%9C%EA%B5%AC%EB%A7%A4%EC%98%88%EC%B8%A1%EB%AA%A8%ED%98%95/Images/%EA%B5%AC%EB%A7%A4%EC%98%88%EC%B8%A1%EB%AA%A8%ED%98%95%ED%88%AC%EC%9E%85%EB%B3%80%EC%88%98%EB%AA%A9%EB%A1%9D.jpg)

- 다양한 에측 기법의 비교 및 최적 모델 구축을 위해 이진분류에 많이 사용되는 모델인 **의사결정나무(Decision Tree), 랜덤 포레스트(Random Forest), XGBoost모델**을 활용해 비교하고, **보팅 분류기(Voting Classifier)** 를 사용해 최종 모델을 결정
- 모델 분류 성능 측정 방법은 이진 분류의 예측 성능에서 중요하게 사용되는 **ROC-AUC Score**. 이진분류(재구매 여부 0,1)의 경우 데이터의 구성에 따라 머신러닝 모델의 성능이 왜곡될 수 있고, 실제 구매하지 않은 고객을 구매한 고객으로 판단했을 때 구매 예측 모형 해석 및 활용에 한계가 있으므로 **정밀도(Precision)** 을 고려하여 에측 성능을 보완

## 2. 구매에측모형 결과
※ 향후 재검토 결과 코드에 오류가 발견되어 이전에 내었던 시각화 자료와 다를 수 있음

### A. 의사결정나무(Decision Tree)
- Confusion Matrix  
![의사결정나무예측성능](https://github.com/chIorophyII/ArtCenter_Project/blob/main/Code/%EA%B8%B0%EA%B3%84%ED%95%99%EC%8A%B5%EC%9D%84%ED%99%9C%EC%9A%A9%ED%95%9C%EA%B5%AC%EB%A7%A4%EC%98%88%EC%B8%A1%EB%AA%A8%ED%98%95/Images/DecisionTreeConfusionMatrix.png)  
- ROC Curve  
![의사결정나무ROC곡선](https://github.com/chIorophyII/ArtCenter_Project/blob/main/Code/%EA%B8%B0%EA%B3%84%ED%95%99%EC%8A%B5%EC%9D%84%ED%99%9C%EC%9A%A9%ED%95%9C%EA%B5%AC%EB%A7%A4%EC%98%88%EC%B8%A1%EB%AA%A8%ED%98%95/Images/DecisionTreeROC.png)  
- Precision / Recall  
![의사결정나무정밀도재현율](https://github.com/chIorophyII/ArtCenter_Project/blob/main/Code/%EA%B8%B0%EA%B3%84%ED%95%99%EC%8A%B5%EC%9D%84%ED%99%9C%EC%9A%A9%ED%95%9C%EA%B5%AC%EB%A7%A4%EC%98%88%EC%B8%A1%EB%AA%A8%ED%98%95/Images/DecisionTreePrecisionRecall.png)  
- Feature Importance  
![의사결정나무변수중요도](https://github.com/chIorophyII/ArtCenter_Project/blob/main/Code/%EA%B8%B0%EA%B3%84%ED%95%99%EC%8A%B5%EC%9D%84%ED%99%9C%EC%9A%A9%ED%95%9C%EA%B5%AC%EB%A7%A4%EC%98%88%EC%B8%A1%EB%AA%A8%ED%98%95/Images/DecisionTreeFeatureImportance.png)  

### B. 랜덤포레스트(Random Forest)
- Confusion Matrix  
![랜덤포레스트예측성능](https://github.com/chIorophyII/ArtCenter_Project/blob/main/Code/%EA%B8%B0%EA%B3%84%ED%95%99%EC%8A%B5%EC%9D%84%ED%99%9C%EC%9A%A9%ED%95%9C%EA%B5%AC%EB%A7%A4%EC%98%88%EC%B8%A1%EB%AA%A8%ED%98%95/Images/RandomForestConfusionMatrix.png)  
- ROC Curve  
![랜덤포레스트ROC곡선](https://github.com/chIorophyII/ArtCenter_Project/blob/main/Code/%EA%B8%B0%EA%B3%84%ED%95%99%EC%8A%B5%EC%9D%84%ED%99%9C%EC%9A%A9%ED%95%9C%EA%B5%AC%EB%A7%A4%EC%98%88%EC%B8%A1%EB%AA%A8%ED%98%95/Images/RandomForestROC.png)
- Precision / Recall  
![랜덤포레스트정밀도재현율](https://github.com/chIorophyII/ArtCenter_Project/blob/main/Code/%EA%B8%B0%EA%B3%84%ED%95%99%EC%8A%B5%EC%9D%84%ED%99%9C%EC%9A%A9%ED%95%9C%EA%B5%AC%EB%A7%A4%EC%98%88%EC%B8%A1%EB%AA%A8%ED%98%95/Images/RandomForestPrecisionRecall.png)  
- Feature Importance  
![랜덤포레스트변수중요도](https://github.com/chIorophyII/ArtCenter_Project/blob/main/Code/%EA%B8%B0%EA%B3%84%ED%95%99%EC%8A%B5%EC%9D%84%ED%99%9C%EC%9A%A9%ED%95%9C%EA%B5%AC%EB%A7%A4%EC%98%88%EC%B8%A1%EB%AA%A8%ED%98%95/Images/RandomForestFeatureImportance.png)  

### C. XGBoost
- Confusion Matrix  
![XGBoost예측성능](https://github.com/chIorophyII/ArtCenter_Project/blob/main/Code/%EA%B8%B0%EA%B3%84%ED%95%99%EC%8A%B5%EC%9D%84%ED%99%9C%EC%9A%A9%ED%95%9C%EA%B5%AC%EB%A7%A4%EC%98%88%EC%B8%A1%EB%AA%A8%ED%98%95/Images/VotingClassifierAccuracy.png)  
- ROC Curve  
![XGBoostROC곡선](https://github.com/chIorophyII/ArtCenter_Project/blob/main/Code/%EA%B8%B0%EA%B3%84%ED%95%99%EC%8A%B5%EC%9D%84%ED%99%9C%EC%9A%A9%ED%95%9C%EA%B5%AC%EB%A7%A4%EC%98%88%EC%B8%A1%EB%AA%A8%ED%98%95/Images/XGBoostROC.png)  
- Precision / Recall  
![XGBoost정밀도재현율](https://github.com/chIorophyII/ArtCenter_Project/blob/main/Code/%EA%B8%B0%EA%B3%84%ED%95%99%EC%8A%B5%EC%9D%84%ED%99%9C%EC%9A%A9%ED%95%9C%EA%B5%AC%EB%A7%A4%EC%98%88%EC%B8%A1%EB%AA%A8%ED%98%95/Images/XGBoostPrecisionRecall.png)  
- Feature Importance  
![XGBoost변수중요도](https://github.com/chIorophyII/ArtCenter_Project/blob/main/Code/%EA%B8%B0%EA%B3%84%ED%95%99%EC%8A%B5%EC%9D%84%ED%99%9C%EC%9A%A9%ED%95%9C%EA%B5%AC%EB%A7%A4%EC%98%88%EC%B8%A1%EB%AA%A8%ED%98%95/Images/XGBoostFeatureImportance1.png)  
![XGBoost변수중요도2](https://github.com/chIorophyII/ArtCenter_Project/blob/main/Code/%EA%B8%B0%EA%B3%84%ED%95%99%EC%8A%B5%EC%9D%84%ED%99%9C%EC%9A%A9%ED%95%9C%EA%B5%AC%EB%A7%A4%EC%98%88%EC%B8%A1%EB%AA%A8%ED%98%95/Images/XGBoostFeatureImportance2.png)

### D. Voting Classifier
- 모델별 예측 정확도  
![VotingClassifierAccuracy](https://github.com/chIorophyII/ArtCenter_Project/blob/main/Code/%EA%B8%B0%EA%B3%84%ED%95%99%EC%8A%B5%EC%9D%84%ED%99%9C%EC%9A%A9%ED%95%9C%EA%B5%AC%EB%A7%A4%EC%98%88%EC%B8%A1%EB%AA%A8%ED%98%95/Images/VotingClassifierAccuracy.png)

## 3. 결론
- 여러 모델 중 가장 정확도가 높은 XGBoost를 구매예측모형으로 채택
- 다양한 모델의 변수중요도를 종합해 봤을 때, **마지막 티켓 구매 후 경과일(최근 구매 고객), 회당 평균 티켓 구매 수, 대관 공연 비중, 교향곡 구매 비중** 등이 중요한 변수로 파악됨

