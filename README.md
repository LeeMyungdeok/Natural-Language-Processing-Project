# Natural-Language-Processing-Project

<br>
<p align="center">
<img width="500" alt="image" src="https://github.com/LeeMyungdeok/Natural-Language-Processing-Project/assets/115915362/f522681a-8508-443e-b590-5c42ad712bd5">
<br>
<img src= "https://img.shields.io/badge/Javascript-F7DF1E?style=flat-square&logo=JavaScript&logoColor=white" />
<img src= "https://img.shields.io/badge/mongodb-47A248?style=flat-square&logo=mongodb&logoColor=white" />
<img src= "https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=CSS3&logoColor=white" />
<img src= "https://img.shields.io/badge/inux-FCC624?style=flat-square&logo=linux&logoColor=white" />
<img src= "https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=Python&logoColor=white" />
<img src= "https://img.shields.io/badge/fastapi-009688?style=flat-square&logo=fastapi&logoColor=white" />
<img src= "https://img.shields.io/badge/react-61DAFB?style=flat-square&logo=react&logoColor=white" />
<img src= "https://img.shields.io/badge/openai-412991?style=flat-square&logo=openai&logoColor=white" />

<br>
</p>

## 주제 선정 이유
우선적으로 OpenAI API를 활용한 챗봇 프로젝트를 시작으로, 생성형 AI의 다양한 활용 가능성을 깨닫게 되었습니다. 이로써, 개발자로서 항상 꿈꿔왔던 교육 플랫폼을 개발하게 되었습니다. 교육의 평등한 접근성을 실현하기 위해 OpenAI를 활용하여 교육의 공급자 역할을 수행하고 있습니다. 현재는 청소년을 대상으로 한 교육 플랫폼을 운영 중이지만, 미래에는 다양한 교육 형태를 지원할 수 있는 플랫폼을 개발할 것으로 기대합니다.

### 주어진 데이터를 학습하는 생성형 AI를 만들기까지
또한, PDF 파일을 포함한 다양한 데이터 소스를 활용하기 위해 작업을 진행하였습니다. 사용자가 제공한 데이터를 학습하고 값을 생성하기 위해서 데이터 파싱 작업이 필수적입니다. 텍스트 파일은 보통 잘 읽히지만, 데이터의 다양성을 확장하기 위해 PDF 파일도 학습 가능하도록 처리하였습니다. 이러한 데이터 처리 작업이 데이터 임베딩에 미치는 영향을 파악하고, 다양한 라이브러리를 실험하여 한국어에 최적화된 작업을 수행하였습니다. 데이터 파싱 후 데이터를 적절히 분할하고 정리하는 작업은 Langchain을 활용하였으며, 그 이후의 임베딩 작업은 OpenAI를 통해 수행되었습니다.
또한, 임베딩된 데이터는 Weaviate 저장소에 보관되며, OpenAI의 언어 모델을 활용하여 사용자 요청에 따라 Vectorstore에 저장된 데이터에서 정보를 추출하고 생성합니다. 이를 통해 사용자에게 더 나은 서비스와 경험을 제공하고 있습니다.

### 생성된 결과값을 client 연결
문제를 생성한 결과를 MongoDB에 보관하는 것은 다양한 이유로 결정된 선택입니다. 이 선택에는 여러 가지 고려 사항이 있습니다.
먼저, AI가 생성한 값의 정확성을 보장하기가 어려운 경우가 있습니다. 인공지능은 학습 데이터와 모델의 복잡성에 따라 예측이나 생성한 결과를 신뢰할 수 없을 때가 있습니다. 이런 경우에는 결과를 유연하게 저장하고 검토할 필요가 있습니다. 관계형 데이터베이스는 데이터 스키마를 미리 정의해야 하기 때문에 이러한 상황에 적합하지 않을 수 있습니다. 그 대안으로 NoSQL 데이터베이스인 MongoDB를 선택하는 것은 데이터 구조의 유연성을 제공하며, 결과 값을 저장하기에 적합한 선택입니다.

또한, MongoDB는 문서 지향 데이터베이스로서, JSON 형식과 유사한 BSON(Binary JSON) 형식으로 데이터를 저장합니다. 이는 Python과 같은 프로그래밍 언어와의 통합을 용이하게 만들어줍니다. 결과 값을 MongoDB에 저장하면 Python 웹 프레임워크인 FastAPI를 사용하여 쉽게 조회하고 처리할 수 있습니다.

요약하면, MongoDB를 사용하여 문제 생성 결과를 저장하는 것은 데이터의 유연성과 Python 기반 웹 애플리케이션 개발의 용이성을 고려한 결정입니다. 이를 통해 AI 생성 값의 추론과 관리를 효과적으로 수행할 수 있습니다.

### development environment

#### Recipe-provided-project
```
json-server --watch ./bin_FoodData.json --host 0.0.0.0 --port 5000
```
```
json-serve
```
```
r --watch ./Trash.json --host 0.0.0.0 --port 5001
```

#### server
```
uvicorn main:app --host 0.0.0.0 --port 3000 --reload
```

#### client
```
nodemon app.js
```

## back-end 아키텍쳐 설계

<img width="700" alt="image" src="https://github.com/LeeMyungdeok/Natural-Language-Processing-Project/assets/115915362/b21ee2ff-3d60-4b5b-aaa3-9deb467149d0">


### 기능 동작
|                sign in              |                sign up               |
| :----------------------------------: | :----------------------------------: | 
| <img src='https://github.com/LeeMyungdeok/Recipe-provided-project/assets/115915362/0a8dd09a-962c-4eb5-9ee7-aea4d4bcc16f' width='400px' height='300px'> | <img src='https://github.com/LeeMyungdeok/Recipe-provided-project/assets/115915362/96fccd2d-74b5-4c75-9f83-2857754edf8d' width='400px' height='300px'>                                 |

|                return              |                rental               |
| :----------------------------------: | :----------------------------------: |
| <img src='https://github.com/LeeMyungdeok/Recipe-provided-project/assets/115915362/b6b795d0-f00b-4429-8351-fe532fa74a7c' width='400px' height='300px'> | <img src='https://github.com/LeeMyungdeok/Recipe-provided-project/assets/115915362/36730ab2-37b2-4ecf-8324-3318801bfbc4' width='400px' height='300px'> |

## 배포

예정 입니다.

## 팀명: 이세계식당

* [팀원](링크) - 이명덕, 서민희

## 담당 업무

- backend
  - 공공 데이터 포털에서 요리 재료에 대한 데이터를 가공했습니다.
    - 재료에 대한 전처리는 주로 코넬파이를 이용하여 형태소 분리 또는 정규 표현식을 사용하여 작업을 진행했습니다. 
  - 요리 레시피에 대한 데이터 및 재료 데이터를 가지고 Fast api를 사용하여 Rest full 방식으로 프로세스를 구축했습니다.
    - json 파일을 임의의 server로 사용하여 전처리를 잘못된부분을 필터링을 걸치도록 하기위해 구축했습니다.
    - 검색, 연관검색, 신고, 레시피 조회 등 전반적인 api 설계 부터 구현까지 위주로 담당업무를 진행했습니다. 
- frontend
  - xhr를 사용하여 client와 server을 연결했습니다.
    - 기존에 axios를 사용했지만 xhr을 알게 되어 어떤 흐름으로 가는지 경험했습니다. 
 
## 보완점

* 데이터 전처리에 대한 경우 완벽하지 못하여 재료가 아닌 값이 나오는 경우가 있습니다. 그것을 사용자가 신고를 해줌으로써 필터안에 들어가게 되고 그 후 다시 그 음식에 대한 레시피를 조회하면 필터링이 될 수 있도록 설계를 했습니다. 비롯 초반에는 애러가 종종 발생하지만 사용자들이 사용하고 신고를 눌러 줌으로써 데이터가 쌓여 더욱 정교한 프로세스서가 될수 있는 성장형 프로그램을 만들었습니다.
* 현재 AWS에서 다시 Develop 예정입니다.
