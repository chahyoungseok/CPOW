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
    <li>
      <a href="#본문-내용">본문 내용</a>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
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
