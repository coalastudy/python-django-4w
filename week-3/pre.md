---
description: >-
  반복적이거나 타이핑의 양이 많아 효율성을 저하시키는 코드를 모아 필요시 복사&붙여넣기할 수 있도록 준비하였습니다. 시간이 충분하다면 처음부터
  끝까지 직접 타이핑하며 완성하는게 좋습니다. 주로 시간이 한정되어있는 스터디 중에 이용됩니다.
---

# Pre - 실습 코드 복사

## Stage 1 - 함께하는 페이스북 디자인

### 형태 잡기  <a id="15p"></a>

#### 강의자료 10page  <a id="10p"></a>

{% code-tabs %}
{% code-tabs-item title="newsfeed.html" %}
```markup
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <title>뉴스피드</title>
</head>

<body>
    <style>
    </style>
    <div class="header">
        <div class="btn1">버튼1</div>
        <div class="search">
            <input type="text" class="searchbar" placeholder="Search">
        </div>
        <div class="btn2">버튼2</div>
    </div>
    <div class="container">
        내용물
    </div>
    <div class="footer">
        <div class="tab1">탭1</div>
        <div class="tab2">탭2</div>
        <div class="tab3">탭3</div>
        <div class="tab4">탭4</div>
    </div>
</body>

</html>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

####  강의자료 11page  <a id="11p"></a>

{% code-tabs %}
{% code-tabs-item title="newsfeed.html의 style 부분" %}
```markup
<style>
    .header {
        background-color: #475d9f;
        color: #fff;
    }
    .container {
        background-color: #d7d8dc;
    }
    .footer {
        background-color: gray;
    }
</style>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

#### 강의자료 13page  <a id="13p"></a>

{% code-tabs %}
{% code-tabs-item title="newsfeed.html의 style 부분" %}
```markup
<style>
    .header {
        background-color: #475d9f;
        color: #fff;
        border-bottom: 1px solid #2c3863;
        height: 50px;
    }
    .btn1 {
        position: absolute;
        left: 10px;
    }
    .search {
        position: absolute;
        left: 100px;
        right: 100px;
   }
    .btn2 {
        position: absolute;
        right: 10px;
    }
    .container {
        background-color: #d7d8dc;
        height: 500px;
    }
    .footer {
        background-color: gray;
    }
</style>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

#### 강의자료 14page  <a id="14p"></a>

{% code-tabs %}
{% code-tabs-item title="newsfeed.html의 style 부분" %}
```markup
<style>
    .header {
        background-color: #475d9f;
        color: #fff;
        border-bottom: 1px solid #2c3863;
        height: 50px;
    }
    .btn1 {
        position: absolute;
        left: 10px;
    }
    .search {
        position: absolute;
        left: 100px;
        right: 100px;
   }
    .btn2 {
        position: absolute;
        right: 10px;
    }
    .container {
        background-color: #d7d8dc;
        height: 500px;
    }
    .footer {
        border-top: 1px solid #cccccc;
        background-color: #ffffff;
        height: 50px;
    }
    .tab1 {
        float: left;
    }
    .tab2 {
        float: left;
    }
    .tab3 {
        float: left;
    }
    .tab4 {
        float: left;
    }
</style>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

####  강의자료 15page  <a id="15p"></a>

{% code-tabs %}
{% code-tabs-item title="newsfeed.html의 style 부분" %}
```markup
<style>
    .header {
        background-color: #475d9f;
        color: #fff;
        height: 50px;
        border-bottom: 1px solid #2c3863;
    }
    .btn1 {
        position: absolute;
        left: 10px;
    }
    .search {
        position: absolute;
        left: 100px;
        right: 100px;
    }
    .searchbar {
        border: 1px solid #2c3863;
        background-color: #323f6b;
    }
    .btn2 {
        position: absolute;
        right: 10px;
    }
    .container {
        background-color: #d7d8dc;
        height: 500px;
    }
    .footer {
        border-top: 1px solid #cccccc;
        background-color: #fafafa;
        height: 50px;
    }
    .tab1 {
        float: left;
    }
    .tab2 {
        float: left;
    }
    .tab3 {
        float: left;
    }
    .tab4 {
        float: left;
    }
</style>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

#### 현재까지 전체 코드

{% code-tabs %}
{% code-tabs-item title="newsfeed.html" %}
```markup
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <title>뉴스피드</title>
</head>

<body>
    <style>
        .header {
            background-color: #475d9f;
            color: #fff;
            height: 50px;
            border-bottom: 1px solid #2c3863;
        }
        .btn1 {
            position: absolute;
            left: 10px;
        }
        .search {
            position: absolute;
            left: 100px;
            right: 100px;
        }
        .searchbar {
            border: 1px solid #2c3863;
            background-color: #323f6b;
        }
        .btn2 {
            position: absolute;
            right: 10px;
        }
        .container {
            background-color: #d7d8dc;
            height: 500px;
        }
        .footer {
            border-top: 1px solid #cccccc;
            background-color: #fafafa;
            height: 50px;
        }
        .tab1 {
            float: left;
        }
        .tab2 {
            float: left;
        }
        .tab3 {
            float: left;
        }
        .tab4 {
            float: left;
        }
    </style>
    <div class="header">
        <div class="btn1">버튼1</div>
        <div class="search">
            <input type="text" class="searchbar" placeholder="Search">
        </div>
        <div class="btn2">버튼2</div>
    </div>
    <div class="container">
        내용물
    </div>
    <div class="footer">
        <div class="tab1">탭1</div>
        <div class="tab2">탭2</div>
        <div class="tab3">탭3</div>
        <div class="tab4">탭4</div>
    </div>
</body>

</html>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

###  디테일 잡기

이미지 다운로드 후 facebook/static 폴더에 넣으셔야 합니다.

**이미지 다운로드** [http://bit.ly/2z4e1rt](https://github.com/coalastudy/python-django-4w/tree/0ee673c3f31128e199767436d8ec2953eb531c3c/2z4e1rt/README.md)

#### 강의자료 17page  <a id="17p"></a>

{% code-tabs %}
{% code-tabs-item title="newsfeed.html" %}
```markup
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <title>뉴스피드</title>
</head>

<body>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; }
        .header {
            background-color: #475d9f;
            color: #fff;
            height: 42px;
            border-bottom: 1px solid #2c3863;
        }
        .btn1 {
            position: absolute;
            left: 0px;
        }
        .search {
            position: absolute;
            left: 50px;
            right: 50px;
        }
        .searchbar {
            border: 1px solid #2c3863;
            background-color: #323f6b;
            width: 100%;
            border-radius: 4px;
            padding: 6px; margin-top: 7px;
            color:#ffffff;
        }
        .btn2 {
            position: absolute;
            right: 0px;
        }
        .container {
            background-color: #d7d8dc;
            height: 500px;
        }
        .footer {
            border-top: 1px solid #cccccc;
            background-color: #fafafa;
            height: 50px;
        }
        .tab1 {
            float: left;
        }
        .tab2 {
            float: left;
        }
        .tab3 {
            float: left;
        }
        .tab4 {
            float: left;
        }
    </style>
    <div class="header">
        <div class="btn1"><img src="/static/ic_pencil.jpg" width="22px" style="margin:9px 0 0 13px"></div>
        <div class="search">
            <input type="text" class="searchbar" placeholder="Search">
        </div>
        <div class="btn2"><img src="/static/ic_info.jpg" width="22px" style="margin:9px 13px 0 0"></div>
    </div>
    <div class="container">
        내용물
    </div>
    <div class="footer">
        <div class="tab1">탭1</div>
        <div class="tab2">탭2</div>
        <div class="tab3">탭3</div>
        <div class="tab4">탭4</div>
    </div>
</body>

</html>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

####  강의자료 18page  <a id="18p"></a>

{% code-tabs %}
{% code-tabs-item title="newsfeed.html" %}
```markup
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <title>뉴스피드</title>
</head>

<body>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body { background-color: #d7d8dc; }
        .header {
            background-color: #475d9f;
            color: #fff;
            height: 42px;
            border-bottom: 1px solid #2c3863;
        }
        .btn1 {
            position: absolute;
            left: 0px;
        }
        .search {
            position: absolute;
            left: 50px;
            right: 50px;
        }
        .searchbar {
            border: 1px solid #2c3863;
            background-color: #323f6b;
            width: 100%;
            border-radius: 4px;
            padding: 6px; margin-top: 7px;
            color:#ffffff;
        }
        .btn2 {
            position: absolute;
            right: 0px;
        }
        .container {
            background-color: #d7d8dc;
        }
        .footer {
            border-top: 1px solid #cccccc;
            background-color: #fafafa;
            height: 50px;
            text-align: center;
            position:fixed; bottom: 0; left: 0; right: 0;
        }
        .tab1 {
            float: left;
            width: 25%;
        }
        .tab2 {
            float: left;
            width: 25%;
        }
        .tab3 {
            float: left;
            width: 25%;
        }
        .tab4 {
            float: left;
            width: 25%;
        }
    </style>
    <div class="header">
        <div class="btn1"><img src="/static/ic_pencil.jpg" width="22px" style="margin:9px 0 0 13px"></div>
        <div class="search">
            <input type="text" class="searchbar" placeholder="Search">
        </div>
        <div class="btn2"><img src="/static/ic_info.jpg" width="22px" style="margin:9px 13px 0 0"></div>
    </div>
    <div class="container">
        내용물
    </div>
    <div class="footer">
        <div class="tab1"><img src="/static/ic_feed.jpg" width="22px" style="margin-top: 15px"> </div>
        <div class="tab2"><img src="/static/ic_person.jpg" width="20px" style="margin-top: 14px"></div>
        <div class="tab3"><img src="/static/ic_globe.jpg" width="20px" style="margin-top: 14px"> </div>
        <div class="tab4"><img src="/static/ic_etc.jpg" width="20px" style="margin-top: 14px"></div>
    </div>
</body>

</html>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

####  강의자료 19~20page  <a id="19p"></a>

{% code-tabs %}
{% code-tabs-item title="newsfeed.html" %}
```markup
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <title>뉴스피드</title>
</head>

<body>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body { background-color: #d7d8dc; }
        .header {
            background-color: #475d9f;
            color: #fff;
            height: 42px;
            border-bottom: 1px solid #2c3863;
        }
        .btn1 {
            position: absolute;
            left: 0px;
        }
        .search {
            position: absolute;
            left: 50px;
            right: 50px;
        }
        .searchbar {
            border: 1px solid #2c3863;
            background-color: #323f6b;
            width: 100%;
            border-radius: 4px;
            padding: 6px; margin-top: 7px;
            color:#ffffff;
        }
        .btn2 {
            position: absolute;
            right: 0px;
        }
        .container {
            background-color: #d7d8dc;
        }
        .footer {
            border-top: 1px solid #cccccc;
            background-color: #fafafa;
            height: 50px;
            text-align: center;
            position:fixed; bottom: 0; left: 0; right: 0;
        }
        .tab1 {
            float: left;
            width: 25%;
        }
        .tab2 {
            float: left;
            width: 25%;
        }
        .tab3 {
            float: left;
            width: 25%;
        }
        .tab4 {
            float: left;
            width: 25%;
        }
        .feed {
            background-color: #ffffff;
            border-top: 1px solid #c0c0c0;
            border-bottom: 1px solid #c0c0c0;
            margin: 7px 0;
            padding: 12px;
        }
        .date {
            color: #999;
            margin-bottom: 10px;
        }
        .title {
            color: #6184dd;
            font-weight: 600;
        }
        .content {
            margin-top: 5px;
        }
        .accessory {
            border-top: 1px solid #eee;
            padding-top:10px;
            margin-top:10px;
            color: #999;
            font-size: 14px;
        }
    </style>
    <div class="header">
        <div class="btn1"><img src="/static/ic_pencil.jpg" width="22px" style="margin:9px 0 0 13px"></div>
        <div class="search">
            <input type="text" class="searchbar" placeholder="Search">
        </div>
        <div class="btn2"><img src="/static/ic_info.jpg" width="22px" style="margin:9px 13px 0 0"></div>
    </div>
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
    <div class="footer">
        <div class="tab1"><img src="/static/ic_feed.jpg" width="22px" style="margin-top: 15px"> </div>
        <div class="tab2"><img src="/static/ic_person.jpg" width="20px" style="margin-top: 14px"></div>
        <div class="tab3"><img src="/static/ic_globe.jpg" width="20px" style="margin-top: 14px"> </div>
        <div class="tab4"><img src="/static/ic_etc.jpg" width="20px" style="margin-top: 14px"></div>
    </div>
</body>

</html>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

##  Stage 2 - 게시글 모델링

### 장고의 모델링  <a id="25p"></a>

{% code-tabs %}
{% code-tabs-item title="models.py" %}
```python
from django.db import models

# Create your models here.
class Article(models.Model):
    author      = models.CharField(max_length=120)
    title       = models.CharField(max_length=120)
    text        = models.TextField()
    password    = models.CharField(max_length=120)
    created_at  = models.DateTimeField(auto_now_add=True)

    def __str__(self):
        return self.title
```
{% endcode-tabs-item %}
{% endcode-tabs %}

