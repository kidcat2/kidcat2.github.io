---
title: "[Blog] 마크다운 작성 시 발생하는 문제와 해결 방법 모음"
date: 2023-10-08 +0000
categories: [Develop, Blog]
tags: [Blog]
---

## Index
1. [블로그 포스트 **비공개** 설정](#1-블로그-포스트-비공개-설정)
2. [이미지 업로드에서 `{: class="left }` 를 했을 때, 이후의 글이 줄바꿈이 되지 않는 경우](#2-이미지-업로드-시-줄바꿈이-되지-않고-이미지-오른쪽에-글이-써지는-경우)
3. [블로그 이미지 다듬기](#3-블로그-이미지-다듬기)
4. [접는 글 안에 list 작성하기](#4-접는-글에-list-작성하기)
5. [순서있는 리스트 사이에 줄바꿈 추가하기](#5-순서있는-리스트-사이에-줄바꿈-추가하기)
6. [`<details>` 사용 시 `code block`이 안되는 경우](#6-details-사용-시-code-block이-안되는-경우)
7. [`prompt-` 사용 시 줄바꿈 넣기](#7-prompt--사용-시-줄바꿈-넣기)
8. [글자 가운데 정렬하기](#8-글자-가운데-정렬하기)

---

### 1. 블로그 포스트 `비공개` 설정

mark 다운 문서 작성시에  `published : false `문구를 추가해주면 된다.
```yaml
title : ...
date : ...
categories : ...
tags : ...
published : false
```

---

### 2. 이미지 업로드 시, 줄바꿈이 되지 않고 이미지 오른쪽에 글이 써지는 경우

1.  `<br>` 이용
    <br>을 여러 번 입력하면서 이미지 아래로 글이 써질 때 까지 확인해보기

2. `{:  .w-75 .normal} ` 이용
    여기서 `w-75` 는 넓이 비율을, `normal` 은 위치를 조정하는 것 같다. 

```html
![이미지 설명](path){:  .w-75 .normal} 로 써주면 된다. 
{:  .w-75 .normal} 외에도 .left , .right도 있다.
```

---

### 3. 블로그 이미지 다듬기
이건 CSS를 이용해야 되고, CSS를 전부 정리하기에는 내용도 너무 많고 나도 잘 알지 못한다. 사람들이 좀 많이 쓰는 것들만 시간 될 때 정리해서 적어두기로 했다.

```css
border : pixel size , solid \#color (이미지 테두리 두께 및 색상 지정 - color는 16진수이다.)
border-radius : pixle size (size를 반지름으로 해서 이미지 모서리를 둥글게 다듬기)
ex : {:style="border:3px solid ##ff0000; border-radius: 4px; " }
```

---

### 4. 접는 글에 list 작성하기
```html
<details>
    <summary> 접는 글 이름 </summary>
    <ul>
        <li> 리스트 이름 </li>
        <li> 리스트 이름2 </li>
    </ul>
</details>
```

---

### 5. 순서있는 리스트 사이에 줄바꿈 추가하기

순서있는 리스트를 작성할 때 1번 리스트와 2번 리스트 간격에 줄바꿈을 추가하고 싶은 경우가 있다. 간격이 너무 좁아보인다거나 하는 이유이다.
이 때 `<br>` 을 사용할 경우 list 된 게 풀리면서 두 리스트가 `1,2` 로 보이는 것이 아니라 `1,1` 로 보일 것이다.

해결한 방법은 '들여쓰기' 이다.

`리스트가 풀리는 경우`
```html
1. 가나다라
....
<br>
2. 마바사

>>
1. 가나다라
1. 마바사
로 보인다.
```

`해결 방법`
```html
1. 가나다라
    ....
    <br><br>
2. 마바사
```
이 방법 말고 다른 방법은 아직 모르겠다. 

---

### 6. `<details>` 사용 시 `code block`이 안되는 경우

```html
<details>
 <summary>...</summary>
 code block
</details>
```

위와 같은 구조로 사용할 경우 code block 이 작동하지 않는다. <br>
맨 위의 `<details>` 를 `<details markdown="1">` 로 수정하면 된다.

---

### 7. `prompt-` 사용 시 줄바꿈 넣기

```html
> **라우팅** <br>
> 네트워크의 효율적 이용을 위하여 서로 통신하는 종단 노드들 사이에 네트워크를 통과하는 경로를 찾는 것. <br>
> 어떻게 네트워크에서 가장 효율적인 경로로 데이터를 전송/수신 할 것인가
{: .prompt-info }
```

![Desktop View](/assets/img/Blog-Markdown/1.png)

---

### 8. 글자 가운데 정렬하기

```html
<p style="text-align:right;">Text_content</p>
<h4 style="text-align:center;">H3 that is center aligned</h4>
```