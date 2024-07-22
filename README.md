[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/D1pZhJxu)
# 초 엘리트 집단

## Eleit LIST



| <img src="https://github.com/UpstageAILab3/upstage-ml-regression-ml12/assets/60285169/696a725d-f2da-44e3-9145-ad14764c373d" width="300" height="300">| <img src="https://github.com/UpstageAILab3/upstage-ml-regression-ml12/assets/60285169/e82c70ed-7aaf-43cc-ad03-5e429820e20c" width="300" height="300"> | <img src="https://github.com/UpstageAILab3/upstage-ml-regression-ml12/assets/60285169/65a02ae5-ab11-4295-8f69-f5ddb482718f" width="300" height="300">| <img src="https://github.com/UpstageAILab3/upstage-ml-regression-ml12/assets/60285169/196b8d22-49b0-4432-bf75-c18cc0942159" img="300" height="300">|
| :--------------------------------------------------------------: | :--------------------------------------------------------------: | :--------------------------------------------------------------: | :--------------------------------------------------------------: |
|            [이선호](https://github.com/UpstageAILab)             |            [정동임](https://github.com/UpstageAILab)             |            [허동재](https://github.com/UpstageAILab)             |            [김시연](https://github.com/UpstageAILab)             |
|                            마스코트                             |                      채찍                             |                            리더보드 중독자                           |                            당근                           |  

## 1. Competiton Info

### Overview

- House Price Predition | 아파트 실거래가 예측

House Price Prediction 경진대회는 주어진 데이터를 활용하여 서울의 아파트 실거래가를 효과적으로 예측하는 모델을 개발하는 대회입니다. 

부동산은 의식주에서의 주로 중요한 요소 중 하나입니다. 이러한 부동산은 아파트 자체의 가치도 중요하고, 주변 요소 (강, 공원, 백화점 등)에 의해서도 영향을 받아 시간에 따라 가격이 많이 변동합니다. 개인에 입장에서는 더 싼 가격에 좋은 집을 찾고 싶고, 판매자의 입장에서는 적절한 가격에 집을 판매하기를 원합니다. 부동산 실거래가의 예측은 이러한 시세를 예측하여 적정한 가격에 구매와 판매를 도와주게 합니다. 그리고, 정부의 입장에서는 비정상적으로 시세가 이상한 부분을 체크하여 이상 신호를 파악하거나, 업거래 다운거래 등 부정한 거래를 하는 사람들을 잡아낼 수도 있습니다. 

저희는 이러한 목적 하에서 다양한 부동산 관련 의사결정을 돕고자 하는 부동산 실거래가를 예측하는 모델을 개발하는 것입니다. 특히, 가장 중요한 서울시로 한정해서 서울시의 아파트 가격을 예측하려고합니다.

### Timeline

프로젝트 전체 기간 (2주)
- start date : 7월 9일 (화) 10:00
- end date : 7월 19일 (금) 19:00

### Evaluation

해당 시점의 매매 실거래가를 예측하는 Regression 대회이며, 평가지표는 RMSE(Root Mean Squared Error)를 사용합니다.

![image](https://github.com/user-attachments/assets/a1e5f1bc-28b7-4aa9-807d-a31ceada06d1)

RMSE는 예측된 값과 실제 값 간의 평균편차를 측정합니다. 아파트 매매의 맥락에서는 회귀 모델이 실제 거래 가격의 차이를 얼마나 잘 잡아내는지 측정합니다. 

## 2. Components

### Directory

- _Insert your directory structure_

## 3. Data descrption

### Dataset overview

주요 데이터는 .csv 형태로 제공되며, 서울시 아파트의 각 시점에서의 거래금액(만원)을 예측하는 것이 목표입니다.

학습 데이터는 아래와 같이 1,118,822개이며, 예측해야 할 거래금액(target)을 포함한 52개의 아파트의 정보에 대한 변수와 거래시점에 대한 변수가 주어집니다.

- ![image](https://github.com/user-attachments/assets/4620b855-30ee-4a2f-98fb-863db801518d)


### EDA

- 초기 탐색적 데이터 분석(EDA)에서는 다음과 같은 주요 내용을 확인하였다:

결측치가 많음: 데이터셋에 많은 결측치가 존재함.

높은 상관관계: 많은 피처들 간에 높은 상관관계가 존재함.

중요한 범주형 피처: 예측에 큰 영향을 주는 피처들이 주로 범주형 피처임.

불규칙한 시계열 데이터: 데이터가 시간에 따라 변하지만, 일정한 간격으로 수집되지 않아 일반적인 시계열 분석이 어려움.


- 이 문제들을 해결하기 위해:

특정 위치에 대한 결측치를 외부 자료를 통해 채움 (예: 특정 아파트 단지의 본번, 부번).

불필요하거나 상관관계가 높은 피처들을 제거.

범주형 피처들을 사용 가능한 형태로 변환하고 관련된 새로운 피처를 추가.


### Feature engineering

결측치 처리:
외부 자원을 사용하여 누락된 위치 데이터를 채움.
결측치 채운 후 불필요해진 피처들을 제거.

범주형 피처 변환:
One-hot 인코딩을 고려했으나, 범주형 값의 고차원 문제로 인해 제외.
평균 타겟 인코딩을 사용하여 범주형 구조를 유지하면서 예측력을 제공함.

이상치 탐지 및 제거:
타겟 값을 평방미터당 가격으로 변환하여 이상치를 식별.
시간에 따른 가격 변동률을 계산하여 시간에 따른 가격 성장을 반영한 조정된 타겟 값을 생성.
Z-score 및 IQR 방법을 사용하여 이상치를 탐지, IQR 방법이 더 효과적임을 확인.

피처 추가:
외부 데이터셋(예: 대중교통 데이터)을 사용하여 피처를 추가.
시간에 따른 가격 성장률을 반영한 조정된 타겟 값을 생성.


## 4. Modeling

### Model descrition

LightGBM 모델을 선택. 대용량 데이터셋과 다수의 범주형 피처를 효율적으로 처리할 수 있으며, 강력한 예측 성능을 제공하는 Gradient Boosting 프레임워크를 기반으로 한다.

### Modeling Process

교차 검증:
K-fold 교차 검증과 시계열 분할을 비교.
K-fold가 더 높은 점수를 제공하지만, 신뢰성이 떨어져 시계열 교차 검증을 선호.

과적합 처리:
2023년 데이터를 학습할 때 과적합 문제를 확인.
시간 순서를 반대로 정렬하여 학습함으로써 과적합을 완화.

## 5. Result

### Leader Board

![image](https://github.com/user-attachments/assets/b4e77cd3-983c-40af-b4c4-316b22679c02)
![스크린샷 2024-07-22 오후 1 55 25](https://github.com/user-attachments/assets/2695689c-8a2c-4d01-885a-e24e77f2db17)
![스크린샷 2024-07-22 오후 1 55 54](https://github.com/user-attachments/assets/d470a01f-b084-4eeb-9002-46fc5605b645)
![스크린샷 2024-07-22 오후 3 38 05](https://github.com/user-attachments/assets/07ac405b-ac94-4246-af1c-f8ee00ae1b63)
![스크린샷 2024-07-22 오후 3 44 06](https://github.com/user-attachments/assets/c58a59a1-71d9-4402-a22c-5d25fdcfcc47)



### Presentation

- _Insert your presentaion file(pdf) link_

## etc

### Meeting Log

- [_Insert your meeting log link like Notion or Google Docs_](https://www.notion.so/12-26a6cff2d7774a8eb03af0de69de6d8f)

### Reference

- _Insert related reference_
