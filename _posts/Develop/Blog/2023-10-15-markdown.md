---
title: "[Blog] 마크다운 문법"
date: 2023-10-08 +0000
categories: [Develop, Blog]
tags: [Blog]
math: true
---

## 기록용 

1. [문법정리](https://khw11044.github.io/blog/blog-etc/2020-12-21-markdown-tutorial/)
2. [수식정리](https://khw11044.github.io/blog/blog-etc/2020-12-21-markdown-tutorial2/)
3. [수식정리2](https://velog.io/@d2h10s/LaTex-Markdown-%EC%88%98%EC%8B%9D-%EC%9E%91%EC%84%B1%EB%B2%95)


## 추가 

1. 첨자 + 분수 + 음수 

    - 1-1. 분수 + 아래첨자  
        - $a_{\frac{1}{2}}$  : `$a_{\\frac{1}{2}}$`  

    - 1-2. 분수 + 아래첨자 + 음수 
        - $a_{\frac{-1}{2}}$ : `$a_{\\frac{-1}{2}}$`
        
    - 1-3.아래첨자 + 음수
        - $a_{-1}$ : `$a_{-1}$`
        
    - 1-4. 음수 + 위첨자
        - $a^{-1}$ : `$a^{-1}$`
        
    - 1-5. 음수 + 위첨자 + 분수
        - $2^{-\frac{3}{2}}$ : `$2^{-\\frac{3}{2}}$`
        
    - 1-6. 위첨자 + 분수
        - $2^{\frac{1}{2}}$ : `$2^{\\frac{1}{2}}$`

    <br><br>
    

2. 공백

    - 2-1. 기본
        - 가&nbsp;나  :  `가&nbsp;나`

    - 2-2. 넓은 공백 (LaTex)
        - 가$\quad$나 :  `가$\quad$나`
        
    - 2-3.길이 지정 (LaTex)
        - 가$\hspace{1cm}$나 :  `가$\hspace{1cm}$나`
        
    - 2-4. span 
        - 가<span style="margin-right : 10px"></span>나 : `가<span style="margin-right : 10px"></span>나`
        
   
