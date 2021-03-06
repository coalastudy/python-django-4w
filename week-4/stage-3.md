# Stage 3 - 게시글을 수정, 삭제하는 페이지

지금까지 **글쓰기 기능**을 만들어봤습니다. 이제 글을 수정, 삭제할 수 있도록 해보겠습니다.

## 수정, 삭제 링크 연결

![](../.gitbook/assets/image-106.png)

detail\_feed.html의 118 line 주변부를 다음과 같이 수정합니다.

{% code-tabs %}
{% code-tabs-item title="detail\_feed.html" %}
```markup
<div class="date">{{ feed.created_at }}</div>
<div><a href="/feed/{{ feed.pk }}/edit"><img src="/static/ic_edit.png" height="16px"></a> <a href="/feed/{{ feed.pk }}/remove"><img src="/static/ic_delete.png" height="16px"></a></div>
<span class="title">{{ feed.title }}</span>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 이제 **게시글 자세히 보기페이지**\(ex `http://127.0.0.1/feed/1/`\)에 수정, 삭제 아이콘이 표시됩니다. 이 링크는 `http://127.0.0.1/feed/1/edit` 과 같이 글번호 뒤에 `/edit,` `/remove` 가 붙은 주소로 이동시켜줍니다.

직접 눌러볼까요? 이동은 되는듯 한데 **오류가 발생합니다.** 아직 연결된 페이지가 없기 때문입니다. 그럼 지금부터 연결될 페이지를 만들어보겠습니다. 연결될 페이지 주소는 아래와 같습니다.

`127.0.0.1/feed/{글 번호}/remove    
127.0.0.1/feed/{글 번호}/eidt`

### 실습

#### 1. new\_feed.html을 복사해서 edit\_feed.html, remove\_feed.html을 만들어줍니다.

#### 2. urls.py를 다음과 같이 수정합니다.

{% code-tabs %}
{% code-tabs-item title="urls.py" %}
```python
from facebook.views import remove_feed, edit_feed

urlpatterns = [
    # 상단 생략
    path('feed/<pk>/', detail_feed),
    path('feed/<pk>/remove/', remove_feed),
    path('feed/<pk>/edit/', edit_feed),
    # 이하 생략
]
```
{% endcode-tabs-item %}
{% endcode-tabs %}

#### 3.  views.py에 다음 두 함수를 추가합니다.

{% code-tabs %}
{% code-tabs-item title="views.py" %}
```python
def remove_feed(request, pk):
    return render(request, 'remove_feed.html')

def edit_feed(request, pk):
    return render(request, 'edit_feed.html')
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## 삭제페이지 폼 만들기 연결

삭제페이지의 내용물이 새글쓰기 페이지와 완전히 같은 상태입니다. 삭제에 어울리는 폼으로 변경해보겠습니다.

### 실습

#### 1. 우선 혼자힘으로 아래와 같은 폼을 구성해봅시다.

remove\_feed.html을 열어 다음과 같이 만들어줍시다. 혼자 만들기 어렵다면 2번으로 넘어가도 좋습니다.

![](../.gitbook/assets/image-217.png)

#### 2. views.py를 수정해줍니다.

{% code-tabs %}
{% code-tabs-item title="views.py" %}
```python
def remove_feed(request, pk):
    article = Article.objects.get(pk=pk)
    return render(request, 'remove_feed.html', {'feed': article})
```
{% endcode-tabs-item %}
{% endcode-tabs %}

####  3. remove\_feed.html을 수정합니다.

1번을 혼자 못하신 분은 더 자세히 봐주세요.

{% code-tabs %}
{% code-tabs-item title="remove\_feed.html" %}
```markup
<div class="container">
    <div class="form_box">
        <form method="POST">
            {% csrf_token %}
            <h3>{{ feed.title }} - 삭제하기</h3>
            <input class="input_field" type="password" placeholder="글 비밀번호" name="password"><br>
            <button class="write_button">삭제</button>
        </form>
    </div>
</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

####  4. 새로고침하여 결과확인

### 이해하기

장고에서 모델을 사용해 글을 불러온 후 글 제목을 띄워줍니다.

![](../.gitbook/assets/image-162.png)

## 게시글 수정 페이지 만들기

이제 수정 페이지를 만들어봅시다.

### 실습

#### 1. edit\_feed.html을 열어 다음과 같이 만들어줍시다.

![](../.gitbook/assets/image-155.png)

혼자 힘으로 어렵다면 계속 진행해주세요.

#### 2. views.py를 수정합니다.

{% code-tabs %}
{% code-tabs-item title="views.py" %}
```python
def edit_feed(request, pk):
    article = Article.objects.get(pk=pk)
    return render(request, 'edit_feed.html', {'feed': article})
```
{% endcode-tabs-item %}
{% endcode-tabs %}

####  3. edit\_feed.html을 수정합니다.

{% code-tabs %}
{% code-tabs-item title="edit\_feed.html" %}
```markup
<h3>글 수정하기</h3>
<input class="input_field" type="text" placeholder="글쓴이의 이름은?" name="author" value="{{ feed.author }}"><br>
<input class="input_field" type="password" placeholder="글 비밀번호" name="password"><br>
<input class="input_field" type="text" placeholder="제목을 입력해주세요." name="title"  value="{{ feed.title }}"><br>
<textarea class="textarea_field" placeholder="내용을 입력해주세요." name="content">{{ feed.text }}</textarea><br>
<button class="write_button">수정</button>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

#### 4.  새로고침하여 결과확인

### 이해하기

장고에서 모델을 사용해 글을 불러온 후 수정할 글의 내용을 미리 채워줍니다.

![](../.gitbook/assets/image-99.png)

