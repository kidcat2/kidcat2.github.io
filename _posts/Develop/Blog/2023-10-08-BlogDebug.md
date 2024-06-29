---
title: "[Blog] Debug & Solution"
date: 2023-10-08 +0000
categories: [Develop, Blog]
tags: [Blog, Jekyll, Debug, Blog Error, Github Blog Error,Chirpy 오류]
---

# Index
1. [--- layout: home # Index page --- 오류](#1-layout-home-index-page-message)
2. [JS file not found 오류ERROR `/assets/js/dist/home.min.js' not found.](#2-js-파일이-없다고-뜨는-경우--error-assetsjsdisthomeminjs-not-found)
3. [The following destination is shared by multiple files 오류 (tag)](#3-the-following-destination-is-shared-by-multiple-files-tag)

---

## 1. layout: home Index page Message

Chirpy 테마를 사용하면서 가장 많이 겪고, 가장 많이 뜨는 오류 중 하나이다. 
이 메시지가 뜨는 정말 다양한 원인이 많기 때문에, 그 중 어떤 원인으로 이 오류가 뜨는지 알기 힘들다. 아래 내용을 모두 확인해보길 바랍니다.

1. url 을 입력하지 않은 경우
config.yml 파일에 url 을 보면 처음에 url: "" 으로 되어있다. 여기에 "https://(username).github.io/" 를 입력하면 된다. 
username 에는 블로그 이름이 들어가므로 내 경우에는 url: "https://kidcat2.github.io/" 이 된다.

2. 원래는 블로그 페이지가 잘 나왔으나, commit을 한 이후에 갑자기 나오지 않는 현상
이거에 대해서는 정확한 원인을 모르겠다. 구글링 해 본 결과 Action 에서 Re-Run 을 하면 된다고 한다. 아래 그 글에 대한 링크를 남겨둔다.
[Link](https://delaying.github.io/posts/layouthome/)

3. Git Repository : Setting > Pages > Source : GitHub Actions 설정
아마 가장 많은 원인이 이 문제 떄문일 것이다. 링크를 남겨둔다. 링크에서 `NichtsHsu` 사람의 글을 읽어보면 된다.
[Link](https://github.com/cotes2020/jekyll-theme-chirpy/issues/628) 

4. pages-deploy.yml 의 설정
이건 오류까지는 아닌 것 같은데... 어떤 점에서 문제인지는 잘 모르겠다. 혹시나 해서 글 링크를 남겨둔다.
[Link](https://velog.io/@hashnsalt/Github-Blog-%EB%A7%8C%EB%93%A4%EA%B8%B0-2)

<br>
---

## 2. JS 파일이 없다고 뜨는 경우 : ERROR `/assets/js/dist/home.min.js' not found.

한 개의 파일이 아니라 한 6개 정도의 파일이 없다고 뜬다. 터미널에는 빨간 글씨의 ERROR 가 아닌 하얀 글씨로 뜨는 경우도 있기 때문에 놓치기 쉽다.
왜 안되지? 싶어서 github로 가보면 아래 사진과 같은 ERROR가 보일 것 이다.<br>
![Desktop View](/assets/img/Error/error-nojsfile.png){:style="border:1px solid #eaeaea; border-radius: 7px; padding: 0px;"}

이 문제가 발생한다면 자신의 asstes/js 폴더에 dist 폴더가 있는지 확인해보자. 없다면 아래 순서대로 실행한다.
1. js폴더에 dist 폴더 만들기
2. 터미널에 `NODE_ENV=production npx rollup -c --bundleConfigAsCjs` 입력
3. 위와 같이 하고 Commit을 했는데 해결이 안된다면, dist를 복사해서 github에 직접가서 file upload를 해준다.

1,2번에 대한 실행 링크 [Link](https://kiffblog.tistory.com/233) 
3번에 대한 실행 링크 [Link](https://velog.io/@lzlko/github-%EB%B8%94%EB%A1%9C%EA%B7%B8)

<br>
---

## 3. The following destination is shared by multiple files (tag)

![Desktop View](/assets/img/Error/error-multiple files.png){:style="border:1px solid #eaeaea; border-radius: 7px; padding: 0px;"}

이 오류는 발생할 때가 있고 안할 때가 있다. 그 이유는 나도 모르겠다. <br>
원인은 `tag` 가 대소문자 구별이 안되는 것이다. 예를 들어서 A 글 `tag` 에 `Blog` 라고 적었는데, B 글에 `blog` 라고 적으면 오류가 난다.<br>
따라서 당연하게도 해결책은 하나로 통일 해주면 된다. blog로 쓰던지 Blog로 쓰던지 둘 중 하나로 결정하면 해결된다.<br>

이 오류는 중복되는 문제가 있으면 발생하기 때문에 `tag` 때문이 아니더라도 오류가 날 수 있다.<br>
오류난 위치를 위 사진에 `tags/blog/index.html` 처럼 알려주기 때문에 대충 뭐가 문제인지는 알 수 있으므로 금방 해결할 수 있다.

<br>
---