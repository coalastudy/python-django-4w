# Stage 3 - 관리자 모드 사용해보기

웹서비스는 유저가 보는 페이지도 존재하지만, 일반적인 권한으로는 접근할 수 없는 관리자만의 전용페이지도 존재합니다. 장고에서 기본으로 생성해주는 마법같은 관리자 기능을 사용해보겠습니다.

## 관리자 계정 생성하기

모델링한 내용을 관리할 수 있도록 admin\(관리자 계정\)을 설정합니다.

### 1. 터미널을 엽니다.

터미널이 열리면 `python manage.py createsuperuser` 실행합니다.

![](../.gitbook/assets/image-9.png)

### 2. 관리자 계정의 이름, 비밀번호, 이메일을 설정합니다.

쉽게 잊어버릴 수 있으므로 연습용 프로젝트에서는 아래와 같이 입력할 것을 권장합니다.

`Username: root    
Email address: 입력하지 않고 엔터    
Password: asdf1234`

이때 보안상 이유로 **패스워드는 입력해도 보이지 않습니다.**

이제 `http://127.0.0.1:8000/admin/`으로 접속해보세요. 방금 생성한 아이디와 비밀번호로 로그인합니다.

![&#xAD00;&#xB9AC;&#xC790; &#xD398;&#xC774;&#xC9C0; &#xC811;&#xC18D; &#xC804; &#xB85C;&#xADF8;&#xC778;](../.gitbook/assets/image-296.png)

## 관리자 페이지 둘러보기

로그인 하시면 모델\(즉 데이터베이스\)들을 관리할 수 있는 관리자 페이지가 나타납니다.

![](../.gitbook/assets/image-215.png)

* 일반적으로 웹사이트에는 회원가입 시스템이 있기 때문에 Users와 Groups 모델을 장고에서 자동생성한다. \(이번 스터디에서는 사용하지 않을 예정\)
* Groups, Users를 클릭해보거나 Add, Change 버튼을 눌러보면 관련 모델을 상당히 정교하게 컨트롤할 수 있다.
* 장고를 사용하지 않으면 이러한 관리자 페이지를 개발자가 직접 만들어야 한다. 이때 걸리는 시간만 수개월에 이르기도 한다.

## 한글 버전으로 변경하기

### 1. settings.py를 실행하여 108 line 주변에서 LANGUAGE\_CODE를 찾습니다.

### 2. 다음과 같이 설정합니다.

![](../.gitbook/assets/image-291.png)

### 3. 새로고침 후 확인

![](../.gitbook/assets/image-121.png)

## 관리자 페이지에 모델 추가

처음 관리자 페이지에 접속하면 Groups\(그룹\), Users\(사용자\)라는 모델만 확인할 수 있습니다.

![](../.gitbook/assets/image-188.png)

![](../.gitbook/assets/image-55.png)

이제 직접 만든 모델인 Aricle을 추가해보겠습니다.

### 1. facebook/admin.py를 실행한 후 다음과 같이 수정합니다.

{% code-tabs %}
{% code-tabs-item title="admin.py" %}
```python
from django.contrib import admin

# Register your models here.
from facebook.models import Article
admin.site.register(Article)
```
{% endcode-tabs-item %}
{% endcode-tabs %}

###  2. 새로고침 후 확인합니다.

![](../.gitbook/assets/image-251.png)

## 관리자 페이지를 이용해 게시글 추가하기

### 1. 추가 버튼 클릭

![](../.gitbook/assets/image-128.png)

### 2. 3~4개의 글을 추가해봅니다.

![](../.gitbook/assets/image-214.png)

### 기타 DB 관리

추가 뿐만 아니라 변경, 삭제도 진행하고 고루고루 체험해봅시다. 직접 진행해주세요.

Articles 모델 외에 기본 모델인 Users와 Groups도 과감하게 추가, 수정해봐도 좋습니다.

