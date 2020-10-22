# PUBG Finish Placement Prediction

## Competion

[PUBG Finish Placement Prediction (Kernels Only)](https://www.kaggle.com/c/pubg-finish-placement-prediction)

## 참고 notebook

[EDA for the popular battle royale game PUBG](https://www.kaggle.com/deffro/eda-is-fun)

## Competion 설명

### 개요

PUBG는 100이 계속해서 줄어드는 전투장 속에서 최후의 1인 혹은 1팀이 남을 때 까지 전투를 하는 배틀로얄 FPS 게임이다.  

이 Competion은 Player의 경기 내용에관한 데이터(kills, revives, elo 등등)를 통해 해당 Player의 등수를 예측하고 실제 등수와의 MSE가 가장 작은 모델을 만드는 것이 목표다.

### Data

Train Data : 4446966 x 29    

Test Data : 1934174 x 28  

* **ID** : 플레이어 식별자
* **groupID** : 팀 식별자
* **matchID** : 게임 식별자
* **DBNOs** : 적을 기절시킨 횟수
* **assists** : 죽이진 않았지만 데미지를 준 적의 수
* **boosts** : 부스트 아이템 사용 횟수(진통제, 드링크, 아드레날린 주사)
* **damageDealt** : 총 넣은 데미지 량
* **headshotKills** : 헤드샷 킬 수
* **heals** : 힐 아이템 사용 수(붕대, 구급상자, 키트)
* **killPlace** : 게임 내에서 킬 등수
* **killPoints** : 게임 전체 킬 랭킹(킬만 고려한 랭킹)
* **killStreaks** : 한번의 교전에서의 최다 킬 수
* **kills** : 킬 수
* **longestKill** : 장커리 킬 거리
* **matchDuration** : 경기 시간(초)
* **matchType** : Solo, Duo, Squard
* **rankPoints** : 전체 랭킹(킬 + 승리 모두를 고려한 랭킹)
* **revives** : 동료를 살린 횟수
* **rideDistance** : 차량 이동 거리(meter)
* **roadKills** : 차로 죽인 횟수
* **swimDistance** : 수영한 거리(meter)
* **teamKills** : 팀킬 횟수
* **vehicleDestroys** : 차량 폭파 횟수
* **walkDistance** : 걸어간 거리(meter)
* **weaponsAcquired** : 획득한 무기 종류 갯수
* **winPoints** : 승리 전체 랭킹(승리를 고려한 랭킹)
* **numGroups** : 게임 내 총 그룹 수
* **maxPlace** : 게임내 최악의 등수
* **winPlacePerc** :  Target. 예측 등수를 0.0~1.0사이의 값으로 변환한 값.

Num Groups와 maxPlace의 속성이 조금 애매하다. 모든 데이터에서 maxPlace >= numGroups 인것으로 보아 게임 대기방에서 그룹수가 count된 후 나갔기 때문에 약간의 차이가 있는것으로 보인다.  

</br>

### 정리

총 4446966 by 29의 Train Data를 통해 모델을 생성하고, 1934174 개의 test 데이터에대해 MSE값을 측정하면 된다.  분류 문제가 아닌 회귀 문제.



## 중점적으로 본 사항

### 시각화

정제되지 않은 데이터 더미들을 numpy, plot 등등 다양한 라이브러리를 이용해 시각적, 통계적으로 이해하고 분석하는 다양한 방식을 새롭게 배우고 공부해야할 필요성을 느꼈다.

### Feature Engineering

시각화를 통해 완전히 이해한 데이터를 바탕으로 종속적인 속성들을 묶거나 새롭게 변형킬 수도 있다는 것을 배웠다.

## 시각화

### numpy - quantile(), 인덱싱(필요 범위 뽑아내거나 설정)

#### quantile() : 분위수

자료 크기 순위에 따른 위치값이다. 분위수를 통해 **"대다수"** 와 **"이상치"** 를 판별해 시각화, NA값 설정, feature engineering 등을 할 수 있다. 

```python
print("The average person kills {:.4f} players, 99% of people have {} kills or less, while the most kills ever recorded is {}.".format(train['kills'].mean(),train['kills'].quantile(0.99), train['kills'].max()))
```



### 그래프 - countplot(), distplot(), jointplot(), boxplot(), pointplot(), subplot(), heatmap(), pairplot()

## Feature Engineering



# PUBG
# PUBG
