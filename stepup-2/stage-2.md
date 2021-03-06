# Stage 2 - 살아있는 코멘트

## 코멘트 보기 로직 연결

코멘트가 표시될 부분의 html 작업은 이미 이전 스테이지에서 끝냈습니다. 아직은 실제 코멘트가 출력되지 않고 있습니다. 코멘트 모델과 이 html 페이지를 연결하여 실제 코멘트가 보여지는 로직을 완성해봅시다.

### 실습

#### 1. detail\_feed.html을 열어 아래에서 표시된 부분을 추가해줍니다.

![](../.gitbook/assets/image-112.png)

#### 2. 새로고침하여 중간결과를 확인합니다.

![\* &#xAD00;&#xB9AC;&#xC790; &#xD398;&#xC774;&#xC9C0;&#xC5D0;&#xC11C; &#xC0DD;&#xC131;&#xD55C; &#xCF54;&#xBA58;&#xD2B8; &#xAC1C;&#xC218; &#xB9CC;&#xD07C; &#xBC18;&#xBCF5;&#xB428;](../.gitbook/assets/image-5.png)

#### 3. 표시된 다음 부분을 수정해줍니다.

![](../.gitbook/assets/image-293.png)

#### 4. 새로고침하여 결과를 확인합니다.

![\* &#xC2E4;&#xC81C; &#xCF54;&#xBA58;&#xD2B8; &#xB0B4;&#xC6A9; &#xBC18;&#xC601;&#xB428;](../.gitbook/assets/image-221.png)

### 이해하기

Comment 모델은 Article 모델에 이미 종속되어 있기 때문에 별다른 설정을 해줄 필요가 없습니다. feed라는 Article 1개에 이미 코멘트 정보가 들어가 있으니 불러다 사용만 하면 됩니다.

feed.comments.all 이안에는 이미 해당 글에 대한 모든 코멘트가 불러져 있으므로 우리는 앞서 newsfeed를 출력했던 방식을 사용해 똑같이 코멘트를 출력해줍니다.

![](../.gitbook/assets/image-230.png)

## 코멘트 쓰기 폼 만들기

코멘트를 입력하려면 관리자 페이지에서 직접하는 수밖에 없습니다. 유저들도 코멘트를 입력할 수 있게 만들어줘야겠죠.

### 실습

#### 1. 다음 코드를 `<div class=“comment_list”></div>` 안쪽의 `{% endfor %}` 밑에 넣어줍니다.

{% code-tabs %}
{% code-tabs-item title="detail\_feed.html" %}
```markup
<div>
    <span>Comments</span>
    <form action="" method="POST">
        {% csrf_token %}
        <input type="text" name="author" placeholder="이름" /><br/>
        <input type="password" name="password" placeholder="비밀번호" /><br/>
        <textarea name="text" placeholder="코멘트 내용"></textarea>
        <button type="submit">등록</button>
    </form>
</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

####  2. 새로고침하여 중간결과를 확인합니다.

![](../.gitbook/assets/image-149.png)

#### 3. 코드의 다음 부분을 수정합니다.

![](../.gitbook/assets/image-44.png)

#### 4. 새로고침하여 중간결과를 확인합니다.

![](../.gitbook/assets/image-225.png)

#### 5. Comments 글씨체를 수정해봅시다. 자율적으로 해도 좋으며 강의자료를 따라해도 좋습니다.

![](../.gitbook/assets/image-25.png)

{% code-tabs %}
{% code-tabs-item title="detail\_feed.html 안 style에 추가될 부분" %}
```markup
.help {
    font-size: 14px;
    color: #666;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

####  6. 새로고침하여 결과를 확인합니다.

![](../.gitbook/assets/image-226.png)

### 이해하기

스타일 작업을 한적도 없는데 html 코드를 넣자마자 코멘트 창의 디자인까지 완료되었죠? **어떤 마법을 부린게 아닙니다.** 사실 Stage1에서 코멘트 보기 부분의 html을 작성할 때 style을 추가하였는데요. 이때 이 부분까지 **미리 작업을 해두었기 때문에 가능**한 일입니다. detail\_feed.html에서 `class="form-wrapper"`와 관련된 style을 확인해보세요.

실제 프로젝트에서는 지금처럼 뒤에 작업할 내용까지 미리 만들어 두지는 않습니다. 작게, 쉬운것부터 구조적으로 만들고 **바로바로 화면을 통해 결과를 확인하는 작업의 연속**입니다. 지금은 예외적으로 교육 효율성을 높이기 위해 소량의 스타일 코드를 미리 작업 해둔 상황이었습니다.

하지만 그 style 코드를 살펴보면 이해하기 어려운 부분이 조금 있습니다. 아직 배우지 않았기에 당연히 이해하실 수 없었을 겁니다.

```markup
/* 똑같은 스타일을 적용하고 싶으면 ,를 입력해주면 됩니다. */
.form-wrapper input,
.form-wrapper textarea {
    border: 1px solid #ddd;
    width: 100%;
    padding: 5px;
    font-size: 14px;
    box-sizing: border-box;
    border-radius: 5px;
    margin-top: 2px;
    margin-bottom: 5px;
}

button {
    border: 1px solid #405ea3;
    background-color: #4967ad;
    color: #fff;
    font-weight: 500;
    font-size: 15px;
    padding: 3px 16px;
    border-radius: 2px;
}
```

 **스타일시트** **사용법** **추가학습**

1. **.\(점\)**을 안 붙이면 해당 이름의 모든 태그에 적용됩니다.
2. **,\(콤마\)**를 입력하면 똑같은 스타일을 여러 클래스에 적용할 수 있습니다.
3. **.form-wrapper input** 처럼 **공백**을 넣으면 **.form-wrapper** 안에 있는 모든 **input** 태그들에게 스타일을 입히라는 의미입니다.

자, 이제 이해가 되시?

## 코멘트 쓰기 로직 연결

쓰기 창은 존재하는데 아무리 코멘트를 쓰고 확인버튼을 눌러도 작동이 안되죠? 아직 쓰기 로직을 연결하지 않았기 때문입니다. 이 작업을 마무리해보겠습니다.

### 실습

#### 1. views.py에서 최상단에 다음 코드를 추가합니다.

```python
from facebook.models import Comment
```

####  2. views.py에서 detail\_feed 함수를 찾아 아래와 같이 수합니다.

{% code-tabs %}
{% code-tabs-item title="views.py" %}
```python
def detail_feed(request, pk):
    article = Article.objects.get(pk=pk)

    if request.method == 'POST':  # new comment
        Comment.objects.create(
            article=article,
            author=request.POST.get('author'),
            text=request.POST.get('text'),
            password=request.POST.get('password')
        )

        return redirect(f’/feed/{ article.pk }')

    return render(request, 'detail_feed.html', {'feed': article})
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### 이해하기

코멘트를 생성합니다. 게시글을 생성\(Article\)을 생성하는 원리와 같습니다.

![](../.gitbook/assets/image-213.png)

