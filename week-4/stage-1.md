# Stage 1 - 게시글 쓰기 페이지 만들기

## Form\(폼\)

사용자로부터 입력을 받는 **텍스트필드, 비밀번호 입력창, 내용 입력창** 등을 아울러 Form이라고 합니다. 1주차에서 form 관련 태그를 배운적이 있는데요. 이번 시간부터 본격적으로 사용되는 만큼 복습을 하고 넘어갑시다.

| **Form** **목적** | **Form의** **코드** **사용** **예** |
| :--- | :--- |
| 아이디 입력창 | &lt;input type=“text” placeholder=“아이디를 입력해주세요” &gt; |
| 비밀번호 입력창 | &lt;input type=“password” placeholder=“아이디를 입력해주세요” &gt; |
| 제목 입력창 | &lt;input type=“text” placeholder=“제목을 입력하세요” &gt; |
| 내용 입력창 | &lt;textarea&gt;내용을 입력하세요.&lt;/textarea&gt; |
| 확인 버튼 | &lt;button&gt;게시&lt;/button&gt; |
| 선택 입력 | &lt;input type=“radio” value=“adult”&gt; 성인 &lt;input type=“radio” value=“teen”&gt; 청소년 |
| 체크박스 입력 | &lt;input type=“checkbox” value=“piano” &gt; 피아노 &lt;input type=“checkbox” value=“guitar”&gt; 기타 &lt;input type=“checkbox” value=“drum”&gt;드럼 |

## 실습

### 폼 만들기 준비

127.0.0.1/new 로 연결되는 빈 내용의 게시글 글쓰기 페이지를 만들어보겠습니다.

#### **1. views.py에** **new\_feed** **함수를** **추가합니다.**

{% code-tabs %}
{% code-tabs-item title="views.py" %}
```python
def new_feed(request):
    return render(request, 'new_feed.html')
```
{% endcode-tabs-item %}
{% endcode-tabs %}

####  2. urls.py를 수정합니다.

{% code-tabs %}
{% code-tabs-item title="urls.py" %}
```python
from facebook.views import new_feed

urlpatterns = [
    # 생략
    path('feed/<pk>/', detail_feed),
    path('new/', new_feed),

    # 이하생략
]
```
{% endcode-tabs-item %}
{% endcode-tabs %}

####  3. templates 폴더에 new\_feed.html을 만들고 내용은 detail\_feed.html을 그대로 복붙합니다.

#### 4. 115 line feed 부분을 삭제해주세요.

![](../.gitbook/assets/image-250.png)

### 폼 만들기 연습

방금 코드를 삭제한 부분에 각종 폼을 넣어 다음과 같은 새글쓰기 페이지를 완성해보겠습니다.

![&#xC6B0;&#xC120; &#xD615;&#xD0DC; &#xC7A1;&#xAE30;](../.gitbook/assets/image-135.png)

![&#xCD5C;&#xC885; &#xBAA9;&#xD45C;](../.gitbook/assets/image-290.png)

new\_feed.html에 form을 넣어 형태를 잡습니다.

{% code-tabs %}
{% code-tabs-item title="new\_feed.html" %}
```markup
<div class="container">
    <h3>게시물 올리기</h3>
    <input type="text" placeholder="글쓴이의 이름은?" ><br>
    <input type="password" placeholder=“글 비밀번호" ><br>
    <input type="text" placeholder=“제목을 입력해주세요.” ><br>
    <textarea placeholder="내용을 입력해주세요."></textarea><br>
    <button>게시</button>
</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### 폼 스타일링

#### 1. 폼을 div로 감싸 하얀배경의 박스를 만들 준비를 한 후 각 요소들에 class 이름을 붙여줍니다.

{% code-tabs %}
{% code-tabs-item title="new\_feed.html" %}
```markup
<div class="form_box">
    <h3>게시물 올리기</h3>
    <input class="input_field" type="text" placeholder="글쓴이의 이름은?" ><br>
    <input class="input_field" type="password" placeholder="글 비밀번호" ><br>
    <input class="input_field" type="text" placeholder="제목을 입력해주세요." ><br>
    <textarea class="textarea_field" placeholder="내용을 입력해주세요."></textarea><br>
    <button class="write_button">게시</button>
</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

####  2. 스타일을 입혀 완성도를 높입니다.

{% code-tabs %}
{% code-tabs-item title="new\_feed.html" %}
```markup
.form_box {
    background-color: #ffffff;
    margin: 10px;
    border-radius: 4px;
    border: 1px solid #ddd;
    padding: 10px;
}
.input_field {
    border: 1px solid #ddd;
    border-radius: 4px;
    padding: 4px;
    margin: 3px 0;
    font-size: 14px;
    width: 100%;
}
.textarea_field {
    border: 1px solid #ddd;
    border-radius: 4px;
    padding: 4px;
    margin: 3px 0;
    font-size: 14px;
    width: 100%;
    height: 160px;
}
.write_button {
    background-color: #475d9f;
    border: 1px solid #323f6b;
    color: #ffffff;
    border-radius: 4px;
    padding: 2px 8px;
    font-soze: 18px;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

![&#xACB0;&#xACFC;](../.gitbook/assets/image-220.png)

### 게시글 쓰기 페이지 링크

![](../.gitbook/assets/image-201.png)

#### 1. **‘글쓰기** **버튼’이** **있는** **모든** **페이지를** **수정해야** **합니다.**

* newsfeed.html
* detail\_feed.html
* new\_feed.html

#### 2. 위 파일들을 열고 글쓰기 버튼 코드의 위치를 찾아 a 태그로 링크를 걸어줍니다.

```markup
<div class="btn1">
    <a href="/new"><img src="/static/ic_pencil.jpg" width="22px" style="margin:9px 0 0 13px"></a>
</div>
```

