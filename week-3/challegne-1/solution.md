# 모범 답안

models.py에 다음 코드를 추가한

{% code-tabs %}
{% code-tabs-item title="models.py" %}
```python
# Week 4 - Challenge 1
class Page(models.Model):
    master      = models.CharField(max_length=120)
    name        = models.CharField(max_length=120)
    text        = models.TextField()
    created_at  = models.DateTimeField(auto_now_add=True)

    def __str__(self):
        return self.name
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 터미널에서 `python manage.py makemigrations` 실행, 이어서 `python manage.py migrate`실행합니다.

![](../../.gitbook/assets/image-39.png)

