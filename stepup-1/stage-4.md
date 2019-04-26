# Stage 4 - 장고 구조 살펴보기

장고에서 play\(run 기능\) 버튼을 누르면 신기하게 서버가 작동하죠. 자동으로 페이지도 연결됩니다. 너무 쉽게 되니 마음 한켠이 찜찜할 정도인데요. 실제로 어떤 원리를 통해 페이지가 연결되고 작동하는지 알아보겠습니다.

## 장고의 url, views 원리

장고를 실행시킨다는 것은 서버를 실행시킨다는 의미입니다. 서버가 실행되면 유저들이 내가 만든 웹페이지에 접속할 수 있게 됩니다. \(아직은 외부로 공개는 안해서 자신의 컴퓨터에서만 볼 수 있지요. 외부 공개 작업은 배포라고 부르며 마지막 시간에 진행합니다.\)

### 생성, 수정이 필요한 파일

장고에서 페이지를 표시하려면 **2가지 파일을 수정**하고 **1개의 파일을 생성**합니다.

1. **수정대상** views.py
2. **수정대상** urls.py
3. **생성대상** test.html \(적당한 이름의 html 파일\)

### 원리

그럼 장고상에서 표시되는 html 페이지들이 어떤 원리로 url에 연결되는지 살펴보겠습니다.

![&#xCC28;&#xADFC;&#xCC28;&#xADFC; &#xC0B4;&#xD3B4;&#xBCF4;&#xC138;&#xC694;!](../.gitbook/assets/image-279.png)

## url과 페이지를 연결하는 방법

위에서는 연결 원리에 대해 살펴봤습니다. url과 페이지를 연결하는 방법은 여러번의 실습을 진행했었는데요, 다시한번 복습해보겠습니다.

여태까지는 기계적으로 페이지 생성절차를 익혀왔습니다. 이제 우리는 파이썬과 장고의 원리를 조금이나마 알게 되었고, 이번 복습을 통해 이해없이 따라 진행했던 페이지 연결의 원리를 깨닫게 되실 겁니다.

### `127.0.0.1:8000/play2`로 연결되는 페이지 만들기 복습

스테이지1\(강의자료 9 page\)에서 했던 작업을 다시한번 살펴보겠습니다. 이미 진행했던 실습이니 실제로 한다 생각하고 눈으로 따라오며 이해해주세요. 앞서 만들었던 파일, 내용 확인을 함께 진행한다면 훨씬 수월하게 이해하실 수 있습니다.

#### 1. 무엇을 준비해야하는지 생각해봅시다.

연결될 **페이지 주소**\(url\)과 그 주소에 표시될 **html 파일**이 필요합니다.

**url**: 127.0.0.1:8000/play2  
**html**: templates 폴더에 play2.html을 만들자!

#### 2. play2.html 파일을 templates 폴더안에 생성합니다. templates 폴더를 클릭하고 오른쪽 버튼을 눌러주세요.

![](../.gitbook/assets/image-229.png)

#### 3. views.py안에 play2 함수를 추가합니다.

이어서 play2 함수가 play2.html로 연결되도록 만들어줍니다.

![views.py](../.gitbook/assets/image-129.png)

#### 4. urls.py를 열고 play2 함수를 play2 주소로 연결합니다.

![urls.py](../.gitbook/assets/image-231.png)

#### 결과 확인

![](../.gitbook/assets/image-262.png)

## 장고의 폴더와 파일 설명

아직 다뤄보지 못한 파일도 많고 정체를 모르는 폴더도 많습니다. 규명되지 않은게 있다면 마음이 답답하신 분들이 꼭 있으십니다. **이번만큼은 지적 호기심을 참아달라고 말씀드리고 싶어요.**

장고는 18년 6월 기준으로, **1604명의 개발자들**이 참여하여 **25,819 번의 작업과 회의**를 통해 만들어진 엄청난 프로젝트입니다. 이 안에는 많은 파일과 폴더들이 존재하고 그 규모만큼이나 다양한 사용법이 있습니다.

실제로 장고 개발자들은 이 방대한 프로젝트의 모든 파일과 폴더들을 알지 못하며 모든 사용법도 익히지 못하죠. 실제로는 10~30%만의 기능만으로도 대부분의 장고 프로젝트를 진행할 수 있으니까요. 더군다나 이것들을 모두 암기하기란 불가능에 가깝고 그렇게 할 필요도 없습니다. **메뉴얼이 굉장히 잘 만들어져 있고 수만명이 질문하고 답변한 자료들을 언제든 찾아볼 수 있으니까요.**

이렇게 코딩세계에서는 모든 것을 규명할 필요가 없습니다. 자전거를 타기 위해서 바퀴의 발명 역사를 공부하고 압력에 대해 공부하기 위해 물리책을 사지는 않잖아요? 코딩에서 모르는 부분이 있다면, 쿨하게 남겨두는 것이 좋습니다. 다만 **필요 없기에 무시하는게 아니라 아직은 사용할이 없기 때문에 남겨두는 것**입니다.

![&#xD30C;&#xC774;&#xCC38; &#xC88C;&#xCE21; &#xD504;&#xB85C;&#xC81D;&#xD2B8; &#xD654;&#xBA74;&#xCC3D;](../.gitbook/assets/image-165.png)

| **폴더** **및** **파일명** | **설명** |
| :--- | :--- |
| templates 폴더 | html 파일들을 모아두는 곳 |
| views.py | 특정 페이지 접속시 보여줄 html을 설정하거나 행동을 규정하는 파이썬 파일 |
| urls.py | url 규칙을 작성하는 파이썬 파일 |
| models.py | 데이터베이스 관련 모델설계서를 작성하는 파이썬 파일 |
| admins.py | 관리자를 설정하는 파이썬 파일 |
| migrations 폴더 | 데이터베이스 관련 작업이 있을때 자동으로 생기는 폴더 |
| settings.py | 각종 환경설정\(e.g 한국어/영어 설정\) |
| db.sqlite3 | 데이터베이스 정보가 담겨있는 파일 |
| \*다른 파일들 | 장고를 유지하는데 필수적이지만 실제로 사용할 일은 거의 없음 |

이 정도로만 간략하게 설명하겠습니다. 실제 쓰임새는 앞으로 실습하면서 자연스럽게 알게 될거예요.
