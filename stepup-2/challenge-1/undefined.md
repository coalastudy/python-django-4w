# 모범 답안

detail\_feed.html의 다음 부분을 수정합니다.

{% code-tabs %}
{% code-tabs-item title="detail\_feed.html에서 수정될 부분" %}
```markup
<div class="form-wrapper">
    <span class="help">댓글</span>
    <form action="" method="POST">
        {% csrf_token %}
        <input type="text" name="nickname" placeholder="닉네임" /><br/>
        <input type="password" name="password" placeholder="패스워드" /><br/>
        <textarea name="reply" placeholder="댓글 내용"></textarea>
        <button type="submit">댓글 작성</button>
    </form>
</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 views.py의 다음 함수를 수정합니다.

{% code-tabs %}
{% code-tabs-item title="views.py" %}
```python
def detail_feed(request, pk):
    article = Article.objects.get(pk=pk)

    if request.method == 'POST':  # new comment
        Comment.objects.create(
            article=article,
            author=request.POST['nickname'],
            text=request.POST['reply'],
            password=request.POST['password']
        )

        return redirect(f'/feed/{ article.pk }')

    return render(request, 'detail_feed.html', {'feed': article})
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 

