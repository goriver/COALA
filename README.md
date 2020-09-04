# COALA
국민대 코딱지 프로젝트

## 1. 프로젝트 배경 및 목적

  - 불안한 사회재난 __'싱크홀'__
    - 지반침하은 미세먼지와 더불어 오늘 날 현대인들이 위협적으로 생각하는 재난 중 하나이다. 특히 싱크홀이 도로나 인도등 사람들이 통행하는 곳에서 발생할 경우, 큰 인명피해 
  가 발생할 수 있기 때문에 이를 예방하고, 대비하는 것이 좋다고 생각하였다. 오늘 날 사람들은 미세먼지에 대응하고자 기상상황을 보고 마스크를 챙겨 집을 나선다. 그러나 
  싱크홀의 경우 현재 상황에서는 대응할 방법이 없다. 그저 정부가 집 근처의 노후 시설을 정비해 주기를 기다리는 수밖에 없다. 
    - 따라서 이러한 사회적 필요에 의해 ‘코딱지’는 __머신러닝을 이용한 싱크홀 발생 확률 예측을 진행하기로 하였다.__
  - 싱크홀 관련 어플리케이션의 부재 
    - 친절한 미세먼지 재난 알림음에 비해 미흡한 싱크홀 앱을 확인할 수 있다. 미세먼지 어플은 지역별로 ‘좋음 ‘ 또는 ‘나쁨’ 등 미세먼지 지표를 확실하게 파악 할 수 있는 반면 싱크홀 관련 앱을 살펴보면 싱크홀 앱은 싱크홀이 발생한 지점만 표시해줄 뿐이다. 그래서 우리는 위도, 경도를 입력하면 싱크홀의 위험등급을 알려줄 수 있는 어플을 만들 예정이다. 

  

## 2. 데이터 분석과정 및 방법

- 데이터 수집 출처
- <img src ="https://user-images.githubusercontent.com/50822293/92127752-95fc2680-ee3c-11ea-8eb3-17f44f524d33.png" width="60%"></img>
- 데이터 전처리 및 분석
- <img src ="https://user-images.githubusercontent.com/50822293/92127931-cb087900-ee3c-11ea-83b0-e1d6000833d5.png" width="60%"></img>

  
  ### 1. __상위값으로 전처리__  
    - <img src ="https://user-images.githubusercontent.com/50822293/92128399-5124bf80-ee3d-11ea-981e-1b4f79df7a7a.png" width="60%"></img>
    
    - 지도의 null데이터 처리예시이다. 상위 개념, 예를 들어 서울 노원구 상계동 > 서울 노원구와 같이 null 데이터를 전처리하는 과정을 거쳤다.
  ### 2. __수치형 데이터로 변환__
    - <img src ="https://user-images.githubusercontent.com/50822293/92128677-9648f180-ee3d-11ea-9f3e-a411499981a6.png" width="60%"></img>
    
    - 지질정보의 경우 모델에 이용하기가 어렵다. 이에 누적분포에 따른 양적 변수로 치환함(수치화함)
  ### 3. __box plot을 이용한 이상값 확인__
    - <img src ="https://user-images.githubusercontent.com/50822293/92128766-aeb90c00-ee3d-11ea-9b3d-31a1c915ef2d.png" width="60%"></img>
    
    - 모델에서 잘 학습할 수 있도록 이상값을 확인하고 삭제하는 과정(다는 아니고, 일부)을 거쳤다.
    - 이를 위해 각 feature별 boxplot을 그렸고, 이를 통해 feature선택(변수 선택)의 과정까지 거쳤다.

    ***
    - 더불어 시각화 그래프를 통해 feature중 지질데이터(석회질 암석이 포함된 경우) 와 인공데이터(준공년도, 시추심도) 역시 씽크홀에 영향을 주는 변수라는 것을 파악하였다.
    
## 3. 알고리즘 모델 선택

- ![image](https://user-images.githubusercontent.com/50822293/92129297-49b1e600-ee3e-11ea-839d-1196a257729d.png)
- 여러 알고리즘 모델 테스트 결과 해당 데이터에는 앙상블 모델이 적절하다는 것을 확인하였다. 
