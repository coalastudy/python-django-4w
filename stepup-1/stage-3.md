# Stage 3 - 파이썬으로 장고 깨닫기

## 변수

### 실습 - 변수의 숫자형

```python
a = 1
b = 2
c = -1231
d = -123.53323
sum = 123 + 321
#코드 작성중 쓰다가 메모를 하고 싶다면...
# 앞쪽에 #이 붙어 있으면 실행이 안돼요

print(sum) #결과 444

res = 3 + (2 * 5)
print(res) #결과 13

res = res / 3 #우측변의 계산 결과를 왼쪽에 집어넣는다
print(res) #결과 4.333333333333333

print(1 + 2 -1231) # 결과 -1228
print(a + b + c) # 결과 -1228
```

{% hint style="info" %}
**%는 나머지를 계산해줍니다**  
`print(10 % 3) # 1출력`
{% endhint %}

### 실습 - 변수의 문자열형

```python
a = 'Hello World'
print(a)

b = "Hello World!"
print(b)

a = "Hi~~"
print(a) #a는 원래 'Hello World'지만 덮어 씌울 수도 있어요

b = a
print(b) # b에 a 값을 전해 줄 수도 있어요

longName = '''여러줄에 걸쳐서 글을 쓰려면?
크리스티아누
호날두
두스
산투스
아베이루'''
print(longName)
```

### 실습 - 변수의 리스트형

```python
a = [1, 2, 3, 4]
print(a)
a = [3,5,7]
print(a)

b=[2   ,4,6 , 8 ] # 띄어쓰기의 영향이 없어요
list1 = ['my name', "is", 'django...']
print(list1)

list2 = ['I am', 35, 'years old']
print(list2)

list3 = ['어떤 자료라도 넣을 수 있어요', 100 * 3 + 33, "앞에서 사용한 변수도 넣을 수 있어요", b]
print(list3)

print(list2[0]) # python은 0번부터 순서를 매겨요
print(list2[1])
print(list2[2])
print(list3[3]) # error!
```

### QUIZ

#### 1. 문자를 더하면?

```python
a = 'my name is '
b = 'Django'
print(a + b)
# 문자를 더한 값이 나오겠죠? 
```

#### 2. 문자형에 들어 있는 숫자끼리 더하면?

```python
num1 = '1234'
num2 = '4321'
print(num1 + num2)
#어떤 답이 나올까요? 
```

#### 3. K는 어떤 값이 될까요?

```python
K = 'P'
P = 123
print(K) 
```

#### 답

1. my name is Django
2. 12344321
3. P

## if

### 실습 - 연습

if는 특정 조건에 따라 흐름을 관장하므로 제어문, 조건문이라고도 불립니다.

```python
age = 11
if age > 20:   # age가 20보다 크면?
    print('성인입니다.')

# 여기까지 아무일도 일어나지 않아요

if age <= 19:    #age가 19보다 작거나 같으면?
    print('청소년입니다.')

if age is 100:   #age가 100이면?
    print('백살입니다.')

age = 23
# age를 23으로 변경하고 위의 if문을 그대로 다시 써보세요
```

### 실습 - elif와 else

**elif**는 지금까지 검사한 if, elif가 실행되지 않았을 때, 새로운 조건을 검사합니다.  
**else**는 지금까지 if, elif가 실행되지 않았을 때, 조건 검사 없이 바로 실행합니다.

```python
score = 87
if score >= 70:
    print('통과')
else:
    print("탈락")

if score >= 90:
    print('수')
elif score >= 80:
    print('우')
elif score >= 70:
    print('미')
elif score >= 70:
    print('양')
else:
    print('가')
```

## for

### for란 무엇인가?

어떤 반복적인 일을 하고 싶을때 for문을 사용합니다. for 구문의 사용방법은 아래와 같습니다.

![for&#xBB38;&#xC758; &#xC0AC;&#xC6A9;&#xBC95;](../.gitbook/assets/image-102.png)

```python
# 1부터 100을 출력하고 싶을때
print(1)
print(2)
#...
print(100)
# 백번을 입력해야한다
```

 만약 이때 for문을 사용한다면 다음과 같은 코드만으로도 가능합니다.

```python
for i in range(1, 101): # 1부터 101보다 작은 수까지(=100턴 동안)
    print(i)
    print(i * 2)
```

결과를 예측해보세요. 어떻게 나올까요? \(직접 코딩해서 확인하는게 제일 좋겠죠\)

### list를 for문을 이용해 출력하기

다음과 같은 리스트가 있다고 가정합시다.

`todo_list = ['이따 밥먹기', '빨래하기', 1, 2, 3, '운동하기']`

이 내용물들을 모두 출력하려면 어떻게 해야 할까요? 오늘 배운대로 라면 이렇게 할 수 있습니다.

```python
print(todo_list[0])
print(todo_list[1])
print(todo_list[2])
print(todo_list[3])
print(todo_list[4])
print(todo_list[5])
```

{% hint style="warning" %}
### 헷갈리지 말기

앞서 diary를 출력할할 때 `{{ diray.0 }}` `{{diary.1 }}`과 같은 방식으로 작성했습니다.

그런데 이번에는 `todo_list[0]` `todo_list[1]`와 같은 방식을 사용합니다. 자세한 설명은 **Stage2 도움말**에서 확인해주세요.
{% endhint %}

하지만 너무 반복성이 짙죠. 만약 리스트 내용물이 100개나 있다면, 가히 노가다라 할 만한 작업을 해야할 겁니다. 그나마 100개라면 다행이겠죠.

이러한 반복적인 작업을 대신 수행해주는게 for문입니다. for문을 통해 list를 출력하려면 다음과 같이 입력해주세요.

![for&#xBB38;&#xC5D0;&#xC11C; list &#xC811;&#xADFC;&#xD558;&#xAE30;](../.gitbook/assets/image-286.png)

**todo\_list**라는 이름의 리스트에 접근할 것 입니다. 그리고 그 안에 있는 내용물 하나 하나를 **todo**라고 부르겠습니다. todo는 맨 처음에 todo\_list\[0\]이 되었다가 이어서 todo\_list\[1\]이 됩니다. 그리고 todo\_list\[2\]가 되는 작업을 todo\_list가 끝날때까지 반복합니다. 즉 위에서 노가다로 작업한 print 구문과 똑같은 작업을 한다고 볼 수 있습니다.

### 예시

![](../.gitbook/assets/image-59.png)

### 실습 - list 출력 개선

stage2\(강의자료 17페이지\)에서 for 문을 사용하지 않고 모든 리스트를 각각 출력해봤습니다. 이제 이 부분을 개선시킬 수 있게 됐습니다.

단 차이점은 **장고를 통해 html 에서 for문을 사용한다는 것** 입니다. 이는 **장고의 템플릿 문법**으로 장고가 가지고 있는 특색이자 장점입니다.

```markup
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Play2</title>
</head>
<body>
    {{ name }}님({{ age }}) 안녕하세요? <br>
    {{ cnt }} 번째 방문자이십니다!<br>

    <h2>나의 일기</h2>
    {% for post in diary %}
    <h4>{{ post }}</h4>
    {% endfor %}
</body>
</html>
```

#### 결과확인

![](../.gitbook/assets/image-273.png)

