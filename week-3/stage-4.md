# Stage 4 - 살아있는 뉴스피드

## 게시판 모델과 뉴스피드를 연결

모델도 만들었고, 관리자 모드에서 글도 추가해봤지만 여전히 페이스북은 변함이 없습니다.

![](../.gitbook/assets/image-142.png)

#### 현재 상황

* 관리자 페이지에서 Article에 여러 글을 추가했지만 여전히 페이스북은 변함이 없음
* 지금까지 작업한 것은 껍데기\(외형을 담당하는 html, css\)와 데이터베이스가 저장되는 모델
* 외형과 데이터베이스를 연결하는 작업이 필요

### 실습

#### 1. views.py를 열어 newsfeed 함수를 다음과 같이 수정합니다.

{% code-tabs %}
{% code-tabs-item title="views.py" %}
```python
from django.shortcuts import render
from facebook.models import Article

def newsfeed(request):
    articles = Article.objects.all()

    return render(request, 'newsfeed.html', { 'articles': articles })
```
{% endcode-tabs-item %}
{% endcode-tabs %}

####  2. newsfeed.html에서 108번째 줄 주변 `<div class=“feed”>…</div>`를 찾아 삭제합니다.

![&#xD30C;&#xB780;&#xC0C9; &#xBD80;&#xBD84;&#xB9CC; &#xC0AD;&#xC81C;&#xD574;&#xC8FC;&#xC138;&#xC694;.](../.gitbook/assets/image-11.png)

{% code-tabs %}
{% code-tabs-item title="newsfeed.html" %}
```markup
<div class="container">
    <div class="feed">
        <h3 class="name">이름</h3>
        <div class="date">날짜</div>
        <a class="title">글 제목</a>
        <p class="content">글 내용</p>
        <div class="accessory">
            <img src="/static/ic_like.jpg" width="16px"> Like <img src="/static/ic_comment.jpg" width="16px"> Comments
        </div>
    </div>
</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

####  3. **남아있는** `<div class=“feed”>…</div>` **내부를** **다음과** **같이** **수정합니다.**

{% code-tabs %}
{% code-tabs-item title="newsfeed.html" %}
```markup
<div class="container">
    {% for feed in articles %}
    <div class="feed">
        <h3 class="name">{{ feed.author }}</h3>
        <div class="date">{{ feed.created_at }}</div>
        <a class="title">{{ feed.title }}</a>
        <p class="content">{{ feed.text }}</p>
        <div class="accessory">
            <img src="/static/ic_like.jpg" width="16px"> Like <img src="/static/ic_comment.jpg" width="16px"> Comments
        </div>
    </div>
    {% endfor %}
</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

####  4. 결과확인

![&#xC790;&#xC2E0;&#xC774; &#xAD00;&#xB9AC;&#xC790;&#xD398;&#xC774;&#xC9C0;&#xC5D0;&#xC11C; &#xC791;&#xC131;&#xD55C; &#xAE00;&#xC774; &#xD45C;&#xC2DC;&#xB429;&#xB2C8;&#xB2E4;.](../.gitbook/assets/image-259.png)

#### 5. [`http://127.0.0.1:8000/admin/`](http://127.0.0.1:8000/admin/) 에서 글을 수정하거나 추가한 후 새로고침 해보세요.

### 이해하기

![&#xC22B;&#xC790; &#xBC88;&#xD638;&#xC5D0; &#xB530;&#xB978; &#xC124;&#xBA85;&#xC740; &#xC544;&#xB798;&#xC5D0;&#xC11C; &#xC11C;&#xC220;&#xB429;&#xB2C8;&#xB2E4;.](../.gitbook/assets/image-54.png)

#### 1. 모델에서 데이터 꺼내오기

모델에 저장된 내용을 장고에서 꺼내올 때는 항상 모델명.objects.명령어의 형태로 사용됩니다.

Article.objects.all\(\) Article 모델에서 모든 글을 가져오라는 명령입니다.

#### 2. 모든 게시물이 담긴 articles를 articles라는 이름으로 html로 보내집니다.

#### 3. html에서는 articles라는 이름으로 게시물을 불러올 수 있습니다.

#### 4. 하나 하나의 게시물들은 feed라는 이름으로 처리됩니다.

#### 5. models.py를 열어 Article 모델의 field명을 확인해보세요.

`feed.author`, `feed.created_at`... 등 필드명은 우리가 이미 정의한 것 들입니다. 정의한 것들을 가져다 사용할 뿐입니다.

## 게시글 자세히 보기 링크

![facebook&#xC5D0;&#xC11C; &#xAC8C;&#xC2DC;&#xAE00;&#xC758; &#xB0B4;&#xC6A9;&#xBB3C;&#xC774; &#xAE38; &#xB54C; &#xB098;&#xD0C0;&#xB098;&#xB294; &#x2018;&#xB354;&#xBCF4;&#xAE30;&#x2019; &#xBC84;&#xD2BC;](../.gitbook/assets/image-184.png)

특정 글에대한 자세한 정보를 제공할 수 있도록 **글 제목, 더보기, comments를 눌렀을 때** 게시글 자세히 보기 페이지로 이동시키는게 목표입니다.

![](../.gitbook/assets/image-199.png)

### 실습

#### 1. template 폴더 안에 detail\_feed.html을 생성합니다.

![](../.gitbook/assets/image-28.png)

내용은 임시로 이렇게 채워둡시다.

{% code-tabs %}
{% code-tabs-item title="detail\_feed.html" %}
```markup
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
자세히 보기 페이지 임시
</body>
</html>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

####  2. views.py에 다음 함수를 아래쪽에 추가합니다.

이때 함수 작성 순서는 프로그램에 아무런 영향을 미치지 않습니다. 보기 좋은 위치에 넣어주세요.

{% code-tabs %}
{% code-tabs-item title="views.py" %}
```python
def detail_feed(request, pk):
    article = Article.objects.get(pk=pk)
    return render(request, 'detail_feed.html', {'feed': article})
```
{% endcode-tabs-item %}
{% endcode-tabs %}

####  3. urls.py를 수정합니다.

{% code-tabs %}
{% code-tabs-item title="urls.py" %}
```python
from facebook.views import detail_feed

urlpatterns = [
    …중략

    path('feed/<pk>/', detail_feed)
]
```
{% endcode-tabs-item %}
{% endcode-tabs %}

#### 4. [`http://127.0.0.1:8000/feed/1/`](http://127.0.0.1:8000/feed/1/) [`http://127.0.0.1:8000/feed/2/`](http://127.0.0.1:8000/feed/2/) [`http://127.0.0.1:8000/feed/10/`](http://127.0.0.1:8000/feed/10/) 에 접속해봅니다.

#### 5. newsfeed.html을 열어 a 태그를 수정, 추가해 클릭시 자세히 보기 페이지로 이동되도록 합니다.

{% code-tabs %}
{% code-tabs-item title="newsfeed.html" %}
```markup
<div class="feed">
    <h3 class="name">{{ feed.author }}</h3>
    <div class="date">{{ feed.created_at }}</div>
    <a href="/feed/1" class="title">{{ feed.title }}</a>
    <p class="content">{{ feed.text }} <a class="more" href="/feed/1">더 보기</a></p>
    <div class="accessory">
        <img src="/static/ic_like.jpg" width="16px"> Like <a class="comments" href="/feed/1"><img src="/static/ic_comment.jpg" width="16px"> Comments</a>
    </div>
</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

####  6. 새로고침 해서 확인해봅니다. 스타일시트에 아래 내용도 추가해줍니다.

{% code-tabs %}
{% code-tabs-item title="newsfeed.html" %}
```markup
.more {
    font-size: 14px;
    color: #6184dddd;
}
a {
    color: inherit;
    text-decoration: none;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="info" %}
### `.`을 안붙이고 a 를 쓰면 어떻게 되나요?

스타일 시트에서 `.asdf { }` 은 `<div class="asdf"></div>` 처럼 class 이름이 asdf인 모든 것들에 영향을 미칩니다.

.을 붙이지 않으면 클래스명과 상관없이 태그명에 영향을 미칩니다.

`b { font-size: 50px }` 라고 하면 모든 b 태그가 영향을 받습니다.  
`h1 { font-size: 50px }`, `h3 { font-size: 100px }` 라고하면 각각 h1, h3태그가 영향을 받으며 h1보다 h3의 글자크기가 더 커질 수도 있습니다. 이렇게 태그가 가지고 있는 기본 스타일 속성을 수정하고 싶을 때 .을 제외하고 태그의 이름을 붙입니다.
{% endhint %}

#### 7. 새로고침하여 클릭시 잘 이동이 되나 확인합니다. 잘 된다면, newsfeed.html을 한번 더 수정해줍니다.

{% code-tabs %}
{% code-tabs-item title="newsfeed.html" %}
```markup
{% for feed in articles %}
<div class="feed">
    <h3 class="name">{{ feed.author }}</h3>
    <div class="date">{{ feed.created_at }}</div>
    <a href="/feed/{{ feed.pk }}/" class="title">{{ feed.title }}</a>
    <p class="content">{{ feed.text }} <a class="more" href="/feed/{{ feed.pk }}/">더 보기</a></p>
    <div class="accessory">
        <img src="/static/ic_like.jpg" width="16px"> Like <a class="comments" href="/feed/{{ feed.pk }}/"><img src="/static/ic_comment.jpg" width="16px"> Comments</a>
    </div>
</div>
{% endfor %}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

####  8. 새로고침하여 클릭시 어떤 주소로 이동되는지 확인합니다.

#### 9. detail\_feed.html의 body 부분을 다음과 같이 수정합니다.

{% code-tabs %}
{% code-tabs-item title="detail\_feed.html" %}
```markup
<body>
    <b>글쓴이</b> {{ feed.author }}<br><br>
    <b>날짜</b> {{ feed.date}}<br><br>
    <b>제목</b> {{ feed.title }}<br><br>
    <b>내용</b> {{ feed.text}}
</body>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

####  10. [`http://127.0.0.1:8000/feed/1/`](http://127.0.0.1:8000/feed/1/) 접속하여 확인해봅니다.

![](../.gitbook/assets/image-177.png)

