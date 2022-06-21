# CPOW
### 캡스톤 디자인
<p>
<img src="https://img.shields.io/badge/license-mit-green">
<img src="https://img.shields.io/github/issues/hongjin4790/SYE-project">
<img src="https://img.shields.io/badge/tag-v1.0.0-blue">
<img src="https://img.shields.io/badge/Flask-2C2255?style=flat-square&logo=Flask&logoColor=white"/>
<img src="https://img.shields.io/badge/Ngrok-F8DC75?style=flat-square&logo=Ngrok&logoColor=black"/>
<img src="https://img.shields.io/badge/BlockChain-121D33?style=flat-square&logo=Bitcoin-SV&logoColor=white"/>
<br>
</p>

<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#프로젝트-소개">프로젝트 소개</a>
      <ul>
        <li><a href="#환경-설정">환경 설정</a></li>
      </ul>
    </li>
    <li><a href="#소개">소개</a></li>
    <li><a href="#관련-기술">관련 기술</a></li>
    <li><a href="#본문-소개">본문 소개</a></li>
    <li><a href="#성능-분석">성능 분석</a></li>
    <li><a href="#결론">결론</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgements">Acknowledgements</a></li>
  </ol>
</details>

## 프로젝트 소개
 > 블록체인은 미래의 4차산업혁명을 이끌 기술로 평가된다. 대표적인 합의 알고리즘인 PoW는 탈중앙화와 보안성면에서 장점을 보이지만 에너지 소비량이 많다는 단점이 있다. 따라서 채굴 과정을 단계별로 나누어 채굴 참여자 수를 제한하는 CPoW(Competition Proof Of Work)를 제안한다. 

## 환경 설정
  #### cpow_project : 
     파이썬 인터프리터를 설정해주세요 (conda와 같은 가상환경은 동작하지않습니다.)
     
     console에 "pip install pipenv" "pipenv install" "pipenv install flask" "pipenv install requests" 를 해주세요
     
     그 후 하나의 콘솔창에 "pipenv run python main.py -p 5001" 과 같이 원하는 port를 입력해 구동해주세요 (최소 8개의 console창으로 동작시켜주세요)
     
     postman에서 
     http://localhost:5001/nodes/register
     http://localhost:5002/nodes/register
     http://localhost:5003~5010/nodes/help_nodes
     를 post형식으로 보내주세요

     브라우저에서 http://localhost:5001/allmine을 해주세요. (주의! allmine이 2번 호출되는지 확인해주세요)

     1등노드가 정보공유를 원하지 않는상황을 동작하고싶으시다면 # 악성 노드 : True 를 찾아 True로 바꿔주세요
       위의 상황은 "처음 단 한번만 1등노드가 정보를 공유하지않는다" 라는 상황을 만들었습니다.

  #### CPOWSim :
      파이썬 인터프리터를 설정 후 main에서 동작시켜주세요


## 소개
블록체인은 네트워크를 통해 데이터베이스를 분산해서 관리하는 기술이다. 하나의 중앙집중 서버가 데이터를 관리하는 것이 아닌, p2p 네트워크에 연결된 참여자 모두가 관리한다. 데이터의 유효성 또한 이들에 의해 검증되며 데이터 또한 참여자 모두가 기록하고, 가질 수 있다. 블록체인은 이러한 과정들로 인해 보안성이 높고, 기존의 제 3의 기관을 통해 데이터가 운용될 때에 비해 비용이 절감되며, 서로가 서로를 감시 할 수 있어 신뢰성 또한 높은 기술로 평가된다. <br>
블록체인에서 노드 간 주고받는 데이터간 유효성에 대한 합의는 합의 알고리즘에 의해 이루어진다. 합의 알고리즘을 통해 새 트랜잭션과 블록이 모든 노드가 유효성을 상호 검증함에 의해 블록체인에 연결되고 참여자 모두의 컴퓨터에 분산저장 된다. 합의 알고리즘에는 크게 PoW(작업증명방식)과 PoS(지분증명방식) 이 있다. PoW는 보안성이 높은 반면 느리고, 많은 전력을 소모하고, Pos는 전력소모면에서 이점을 가지는 한편 점유율에 따른 재중앙화를 단점으로 꼽는다. <br>
이에 각 합의알고리즘이 가진 장점을 살리고 단점을 최소화하기 위해 기존의 합의 알고리즘을 재정의하거나 다른 알고리즘과 융합하여 다양한 합의알고리즘 이 고안되어왔다.


## 관련 기술
작업 증명 방식(PoW)을 이해하기 위해서는 우선 마이닝 과정에 대한 개념을 알아야한다. 마이닝(채굴)이란 임의의 nonce 값을 대입하여 블록해시 결과 값을 생성하고, 생성된 결과 값이 제시된 값보다 작은 블록 해시를 찾는 과정이다. 해시를 만들기 위해 해시함수를 사용하는데 해시함수의 특징 때문에 어떤 nonce 값을 대입해야 제시된 값보다 작은 블록해시 정보를 찾을 수 있을지는 알 수 없다. 즉 올바른 결과 값을 찾기 위해서는 nonce값을 1씩 증가시키면서 결과 값이 나올 때까지 무한 반복 작업을 수행해야 한다. 이러한 문제를 푸는 과정을 1초에 몇 번이나 수행할 수 있는지에 대한 수치 정보를 해시파워라고 하고, 해시파워가 높은 채굴자일수록 더 많은 문제를 풀어낼 수 있으며 새로운 블록을 찾을 확률이 더 높다. 해시 파워가 높은 채굴자일수록 많은 일을 수행했다는 의미이고, 더 많은 일을 할 경우 확률적으로 더 많은 보상을 받게 된다. 그렇기 때문에 PoW를 정의할 때 더 많은 일을 한 채굴자에게 더 많은 보상이 주어지는 방식이라고 표현한다. <br>
작업증명 알고리즘의 필요성은 네트워크의 모든 노드가 동시에 블록을 만들 수 없게 하는 것이다. 작업증명에 통과해야만 블록을 생성할 수 있고, 이 과정에서는 엄청난 에너지가 소모된다. 


 ![image](https://user-images.githubusercontent.com/29851990/174717684-ea0cf701-a1fe-4307-ba46-b658dd327ec8.png)


이러한 에너지 소비 문제를 해결하기 위해 CPoW(Competition Proof  of Work)를 제시한다.


## 본문 소개
하나의 블록이 만들어지기 까지의 프로세스는 크게 세 개의 Round로 이루어진다. 첫Round의 채굴연산에서 첫번째로 정답을 도출한 노드는 다른 노드를 통해 검증을 받게 된다. 일반적인 PoW는 검증을 마치고 바로 체인에 블록을 올리지만,  CPoW에서는 블록을 체인에 올리지 않고 전체 노드의 일정 비율만큼의 정답자를 더 받는다. 이 비율을 SNR(Survived Node Rate)라  지정했으며, 한 프로세스 내에 다음 라운드로 넘어가는 과정에서 적용된다. 여기서 SNR은 보안성과 반비례 관계를 가진다.  1등 노드는 모든 노드들의 기준 노드가 되어 어떤노드가 먼저 문제를 풀었나 확인하는 역할을 한다. 이 과정에서 1등노드에 가까이 있는 노드가 네트워크 측면에서 유리할 수 있다. 문제를 해결한 노드들은 검증과정에서 각 노드의 선착순 배열에 들어가게 되며, 이 배열이 식(1)의 과정이 되면 해당 라운드는 종료됨과 동시에 1등노드가 채굴한 블록이 체인에 올라가게 된다. 그리고  선착순 배열에 있는 노드들을 대상으로 다음 round에서 채굴을 진행하며, 총 세 개의  Round 동안 같은 채굴과정을 반복한다. 따라서 한 프로세스 내 총 세 개의 블록이 체결된다. 리워드는 Round 3에서 블록을 체결한 노드가 가지게 된다. 


![image](https://user-images.githubusercontent.com/29851990/174717948-55c19d93-76c6-4f0e-9f25-d00c5dee393c.png) ·································· (1)


## 성능 분석
CPOW방식의 전력소비량 개선을 평가하기 위해 BlockSim-simulator에 CPOW 알고리즘을 적용시켰다.

2019년 기준 한 대의 시스템이 소모하는 전기에너지 소모량은 200wh~800wh라고 한다. 에너지 소모량이 해마다 증가하는 것을 반영하여 전력 소비량의 범위를 600wh ~ 1200wh로 가정한다. 전력 소비량이 최소일 때와 최대일 때를 계산하여 기준선을 그렸고 800wh일때의 환경에서 전력 소비량을 계산했다. 같은 환경에서 CPOW를 사용한다면 그림과 같은 결과가 나오는데 이는 POW의 전력 소비량의 약 46.3%정도이다. 

![image](https://user-images.githubusercontent.com/29851990/174718162-5d22fb5c-eb26-4e5b-b9b1-b74c46e7400d.png)


## 결론
우리는 PoW의 합의과정을 세 단계로 나눔으로써 PoW의 장점은 그대로 유지하되 에너지 소비량을 줄이는 CPoW를 제안했다. 기존의 PoW는 모든 노드가 채굴에 참여하여 엄청난 컴퓨팅 리소스를 사용하기 때문에 이에 천문학적인 에너지 소비가 동원된다. 또한 시간이 지나고 난이도가 높아짐에 따라서 하나의 코인을 얻는데 필요한 에너지는 더 커진다. 이에 CPoW는 채굴 과정을 단계별로 나누어 단계 마다 채굴에 참여하는 노드 수를 일정 비율로 제한시켜 에너지 소비를 줄이는 효과를 볼 수 있다.
