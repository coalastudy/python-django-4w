# 모범 답안

edit\_feed만 수정하시면 됩니다. remove\_feed \(삭제시\)를 참고하면 좋습니다.

{% code-tabs %}
{% code-tabs-item title="views.py" %}
```python
def edit_feed(request, pk):
    article = Article.objects.get(pk=pk)

    if request.method == 'POST':
        if request.POST['password'] == article.password:
            article.author = request.POST['author']
            article.title = request.POST['title']
            article.text = request.POST['content']
            article.save()
            return redirect(f'/feed/{ article.pk }')

    return render(request, 'edit_feed.html', {'feed': article})
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 

