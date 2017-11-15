# CSS Selector



## 선택자(Selector)

```
전체선택자/타입선택자/클래스선택자/아이디선택자/속성선택자/가상요소/가상클래스/하위선택자/형제선택자/인접형제선택자
```

### 전체선택자

전체선택자(Universal Selector)는 모든 HTML요소를 선택합니다. 별표(*)로 나타냅니다.

```css
 1) *{ color : blue; }
 2) *.abc { color: blue; }
 3) .abc { color: blue; }
```

1) 모든 요소의 글씨색 blue
2) .abc 클래스를 가진 모든 요소의 글씨색 blue
3) .abc 클래스를 가진 요소들의 글씨색 blue

### 타입선택자

타입선택자(Type Selector)는 h1, p, div, span등 HTML 요소(element)를 선택하는 선택자입니다.

```css
 1) p { color: blue; }
 2) h1 { color: blue; }
 3) blockquote { font-style: italic; }
```

1) 모든 p태그의 글씨색 blue
2) 모든 h1태그의 글씨색 blue
3) 모든 blockquote태그의 글씨를 기울인다

### class/id 선택자

특정 값을 class 속성(attribute) / id 속성의 값으로 갖는 요소를 선택합니다. 

```css
 1) .abc / #abc
 2) p.abc / div#abc
```

1) class 가 abc / id가 abc인 요소
2) 모든 p태그 중 abc라는 class를 가진 요소 / 모든 div태그 중 abc라는 id를 가진 요소

### 하위선택자

하위선택자(Descendant Selector)는 특정요소 하위에 있는 요소를 선택합니다.

```css
 1) div blockquote (ex. div .test VS div.test )
 2) 선택될까요?
    <div>
       <blockquote>...</blockquote>
    </div>
 3) 선택될까요?
    <div>
       <aside>
          <blockquote>...</blockquote>
       </aside>
    </div>
```

1) 모든 div 요소 안에 있는 모든 blockquote 
​    ex → 모든 div 안에 test라는 클래스를 가진 모든 요소 VS test라는 클래스를 가진 모든 div 요소
2) yes
3) yes

### 자식선택자

자식선택자(Child Selector)는 특정 요소의 자식요소를 선택합니다.

(*하위 선택자와 다른점 : 한 단계 아래에 있는 요소만 선택)

```css
 1) div > blockquote 
 2) 선택될까요?
    <div>
       <blockquote>...</blockquote>
    </div>
 3) 선택될까요?
    <div>
       <aside>
          <blockquote>...</blockquote>
       </aside>
    </div>
```

1) 모든 div 요소 안에 있는 모든 blockquote 
​    ex → 모든 div 안에 test라는 클래스를 가진 모든 요소 VS test라는 클래스를 가진 모든 div 요소
2) yes
3) no

### 형제선택자

형재선택자(Sibling Selector)는 어떤 요소의 형제요소를 선택하는 선택자입니다.

```html
 1) h1 ~ p : h1 요소의 형제 요소 중 p 요소를 선택

 2) 
 <body>
    <h1>Lorem ipsum dolor sit amet.</h1>
    <p>Lorem ipsum dolor sit amet.</p>
    <p>Lorem ipsum dolor sit amet.</p>
    <div>
      <p>Lorem ipsum dolor sit amet.</p>
    </div>
 </body>

```

 Q) 예상되는 결과는?

<body>
   <h1>Lorem ipsum dolor sit amet.</h1>
   **<p>Lorem ipsum dolor sit amet.</p>**
   **<p>Lorem ipsum dolor sit amet.</p>**
   <div>
​       <p>Lorem ipsum dolor sit amet.</p>
   </div>
</body>

### 인접형제선택자

인접 형제 선택자(Adjacent Sibling Selector)는 어떤 요소의 형제요소 중 첫번째 요소를 선택합니다.

```css
 1) h1 + p : h1 요소의 형제 요소 중 첫번째 p 요소를 선택

 2) 
 <style>
   h1 + p {color: red;}
 </style>
 <body>
    <h1>Lorem ipsum dolor sit amet.</h1>
    <p>Lorem ipsum dolor sit amet.</p>
    <p>Lorem ipsum dolor sit amet.</p>
    <div>
      <p>Lorem ipsum dolor sit amet.</p>
    </div>
 </body>
```

Q) 예상되는 결과는?

<body>
   <h1>Lorem ipsum dolor sit amet.</h1>
   **<p>Lorem ipsum dolor sit amet.</p>**
   <p>Lorem ipsum dolor sit amet.</p>
   <div>
​       <p>Lorem ipsum dolor sit amet.</p>
   </div>
</body>

### 속성선택자

속성선택자(Attribute Selector)는 특정속성(attribute)을 갖고있거나 특정 속성이 특정 값등을 갖고 있는 요소를 선택합니다. 

속성선택자는 7가지 형태가 있습니다.

- [attribute]
- [attribute="value"]
- [attribute~="value"]
- [attribute|="value"]
- [attribute^="value"]
- [attribute$="value"]
- [attribute*="value"]

#### [attribute name]

attribute name 속성을 가진 요소를 선택합니다.

```css
h1[title] 
```

→ title 속성을 가진 h1 요소를 선택합니다.

####[attributename="value"]

attribute name 속성의 값이 value인 요소를 선택합니다.

```css
 h1[title="abc"] → title 속성의 값이 abc인 h1 요소를 선택

 1) <h1 title="abc"> Lorem </h1>
 2) <h1 title="abc xyz"> Lorem </h1>
```

**주의 : 속성값이 정확히 일치해야 함!!!****
1) 선택됨
2) 선택되지 않음

#### [attributename~="value"]

attribute name 속성의 값이 value를 포함한 요소를 선택합니다.

```css
 h1[title~="abc"] → title 속성의 값이 abc를 포함한 h1 요소를 선택(포함 여부는 단어 기준)

 1) <h1 title="abc xyz"> Lorem </h1>
 2) <h1 title="abcxyz"> Lorem </h1>
```

1) 선택됨
2) 선택되지 않음

#### [attributename|-"value"]

attribute name속성의 값이 value이거나 value- 로 시작하는 요소를 선택합니다.

```css
 h1[title|="abc"] → title 속성의 값이 abc이거나 abc-로 시작하는 h1 요소를 선택

 1) <h1 title="abc"> Lorem </h1>
 2) <h1 title="abc-xyz"> Lorem </h1>
 3) <h1 title="abc xyz"> Lorem </h1>
```

1) 선택됨
2) 선택됨
3) 선택되지 않음

#### [attributename^="value"]	 *CSS3

attribute name속성이 value로 시작하는 요소를 선택합니다.

```css
h1[title^="abc"] → title 속성의 값이 abc로 시작하는 h1 요소를 선택 (문자열 기준, 단어기준 X)

 1) <h1 title="abc xyz"> Lorem </h1>
 2) <h1 title="abc-xyz"> Lorem </h1>
 3) <h1 title="xyz-abc"> Lorem </h1>
```

1) 선택됨
2) 선택됨
3) 선택되지 않음

```css
1) [class^='btn-s']
2) [class^='btn-m']
```

1) class이름이 btn-s로 시작하는 것을 선택

2)class이름이 btn-m으로 시작하는 것을 선택 

*하이픈으로 해야된다 이유는?-_-;

#### [attributename$="value"]	*CSS3#

attribute name 속성의 값이  value로 끝나는 요소를 선택합니다.

```css
 h1[title$="abc"] → title 속성의 값이 abc로 끝나는 h1 요소를 선택 (문자열 기준)

 1) <h1 title="abc xyz"> Lorem </h1>
 2) <h1 title="abc-xyz"> Lorem </h1>
 3) <h1 title="xyz abc"> Lorem </h1>
 4) <h1 title="xyz-abc"> Lorem </h1>
```

#### [attribute*="value"]	*CSS3

attribute name속성의 값이 value를 포함한 요소를 선택합니다.

```css
h1[title*="abc"] → title 속성의 값이 abc를 포함한 h1 요소를 선택 (문자열 기준)

 1) <h1 title="abc xyz"> Lorem </h1>
 2) <h1 title="abcxyz"> Lorem </h1>
 3) <h1 title="lmn abc-xyz"> Lorem </h1>
 4) <h2 title="xyz-abc"> Lorem </h2>
```

1) 선택됨
2) 선택됨
3) 선택됨
4) 선택되지 않음

###가상요소(Pseudo Element)

가상요소는 요소의 특정부분을 선택합니다.

- ::first-line
- ::first-letter
- ::before
- ::after

→ CSS3부터, 가상 클래스는 콜론을 한 개(:), 가상 요소는 콜론을 두 개(::) 씁니다.
단, IE8 이전은 더블콜론이 지원되지 않고, 대부분의 브라우저에서 콜론을 한 개(:)만 써도 문제가 없으므로 주로 단일 콜론을 사용합니다.

#### ::first-line

::first-line은 요소의 첫번째 줄을 선택합니다.

```css
p::first-line {
   font-weight:bold;
}
```

→ p 요소의 첫번째 줄의 글자색을 굵은글씨로 만듭니다.

<p>

**첫번째 줄 입니다.**
두번째 줄 입니다.

</p>

#### ::first-letter

::first-letter는 요소의 첫번째 문자를 선택합니다.

```css
 p::first-letter {
   font-weight:bold;
 }
```

<p>

**첫**번째 줄 입니다.
두번째 줄 입니다.

</p>

#### ::before

::before는 요소의 앞을 선택합니다.

```css
 p::before {
   content: "xyz";
   font-weight:bold;
 }
```

→ p 요소 앞에 xyz라는 단어를 넣고 굵은글자로 만듭니다.

<p>

 **xyz**첫번째 줄 입니다.
두번째 줄 입니다.

</p>

#### ::after

::after는 요소의 뒤를 선택합니다.

```css
p::after {
   content: "\A 와 white-space:pre를 사용하면 줄바꿈 가능";
   color: red;
 }
```

→ p 요소 뒤에 content에 적은 글자가 빨간색 글씨로 노출됩니다.

<p>

첫번째 줄 입니다.
두번째 줄 입니다.  **백슬러시A와 white-space:pre를**

​                                 **사용하면 줄바꿈가능**

</p>

* 가상요소를 사용하여 붙여넣은 부분은 text로 인식하지 않는 '가상'의 요소
  => 선택하거나 복사 및 붙여 넣기를 할 수 없다. 즉, 드래그로 긁히지 않으며 소스보기에도 나타나지 않는다. 

* 마크업 수정이나 태그/class 추가를 하지 않고서도 사용이 가능하다.

* 줄바꿈/vetical-align속성 다 먹으므로, 아이콘 형식으로도 사용이 가능하다.

* 가상요소를 아이콘 넣는 용도로 사용한 예시 : 
  css 아이콘 예시 : <http://uxuiz.cafe24.com/wp/?p=4726

## 가상클래스(Pseudo-classes)

### :empty

:empty는 내용이 없는 비어있는 요소를 선택합니다.

```css
 <ul class="empty_test">
   <li>내용1</li>
   <li></li>
 </ul>

 .empty_test li:empty{width:50px;height:20px;background:#ccc;}
```

 <ul class="empty_test">
   <li>내용1</li>
   **<li></li>**
 </ul>

###:first-child

:first-child는 형제 요소중 첫번째 요소를 선택합니다.

```
 <ul class="first-child_test">
   <li>요소1</li>
   <li>요소2</li>
   <li>요소3</li>
 </ul>

 .first-child_test li:first-child{color:red;}
```

**요소1**

요소2

요소3

###:nth-child

:nth-child는 형제 요소 중 an+b번째 요소들을 선택합니다.

(지원 브라우저 : Chrome : 4.0, Firefox : 3.5, IE 9.0, Opera : 9.6, Safari : 3.2 이상)

사용법 → **selector:nth-child(an+b){ ... }**

an+b에서 a와 b는 상수로 수의 범위는 정수입니다. n은 변수로 음이 아닌 정수가 차례대로 대입됩니다.

ex) 2n+1은

n이 0 일때, 2 x 0 + 1 = 1

n이 1 일때, 2 x 1 + 1 = 3

n이 2 일때, 2 x 2 + 1 = 5 이므로

:nth-child(2n+1)은 형제 요소 중 1, 3, 5,...번째 요소들을 선택합니다.

```css
 <ul class="nth-child_test">
   <li>요소1</li>
   <li>요소2</li>
   <li>요소3</li>
   <li>요소4</li>
   <li>요소5</li>
 </ul>

 .nth-child_test li:nth-child(2n+1){color:red;}
```

**요소1**

요소2

**요소3**

요소4

**요소5**

Q. 짝수는? 
A.  2n+2

*** an+b의 값이 음수인 경우**
**:nth-child(2n-1)**라면 n이 0일 때 -1입니다. 이 때는 선택할 요소가 없으므로 무시됩니다.
즉, :nth-child(2n+1) 과 같은 결과가 됩니다.

*** an+b에서 a가 0인 경우**
an+b에서 a가 0이라면 b만 남습니다. n이 변해도 무조건 b이므로 하나의 요소만 선택합니다.
**:nth-child(4)**는 형제 요소 중 4번째 요소를 선택합니다.

**even과 odd**
an+b 대신에 even 또는 odd를 넣을 수 있습니다. even은 짝수번째 요소를 선택하고, odd는 홀수번째 요소를 선택합니다.
li:nth-child(odd) {color: red;} → 홀수
li:nth-child(even) {color: red;} → 짝수

### :hover

:hover는 요소에 마우스를 올린 상태를 선택합니다.

```css
   <span>내용1</span>
   <span class="hover_test">내용2</span>

  .hover_test:hover{color: red;}
```

### :not

:not은 특정한 요소를 제외하고 선택할 경우 사용

:not(s)→ s 자리에 부정요소나 가상요소는 올 수 없습니다.



## 선택자 브라우저 지원

### 선택자 브라우저 지원 현황표

| Pattern               | Meaning                                  | S5   | C8   | F3.6 | O11  | I9b  | I8   | I7   | I6   |
| --------------------- | ---------------------------------------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| #id                   | id로 지정된 요소 선택                            | O    | O    | O    | O    | O    | O    | O    | O    |
| .class                | class로 지정된 요소 선택                         | O    | O    | O    | O    | O    | O    | O    | O    |
| E                     | E 요소를 선택                                 | O    | O    | O    | O    | O    | O    | O    | O    |
| E:link                | 방문하지 않은 E를 선택                            | O    | O    | O    | O    | O    | O    | O    | O    |
| E:visited             | 방문한 E를 선택                                | O    | O    | O    | O    | O    | O    | O    | O    |
| E:hover               | 마우스가 올라가 있는 동안 E를 선택                     | O    | O    | O    | O    | O    | O    | O    | O    |
| E:active              | 마우스 클릭 또는 키보드(enter)가 눌린 동안 E를 선택        | O    | O    | O    | O    | O    | O    | O    | X    |
| E:focus               | focus가 머물러 있는 동안 E를 선택                   | O    | O    | O    | O    | O    | O    | X    | X    |
| E:first-line          | E 요소의 첫 번째 라인 선택                         | O    | O    | O    | O    | O    | O    | O    | X    |
| E:first-letter        | E 요소의 첫 번째 문자 선택                         | O    | O    | O    | O    | O    | O    | O    | X    |
| *                     | 모든 요소 선택                                 | O    | O    | O    | O    | O    | O    | O    | O    |
| E[foo]                | ‘foo’ 속성이 포함된 E를 선택                      | O    | O    | O    | O    | O    | O    | O    | X    |
| E[foo=”bar”]          | ‘foo’ 속성의 값이 ‘bar’와 일치하는 E를 선택           | O    | O    | O    | O    | O    | O    | O    | X    |
| E[foo~=”bar”]         | ‘foo’ 속성의 값에 ‘bar’가 포함되는 E를 선택           | O    | O    | O    | O    | O    | O    | O    | X    |
| E[foo\|=”en”]         | ‘foo’ 속성의 값이 ‘en’ 또는 ‘en-‘ 으로 시작되는  E를 선택 | O    | O    | O    | O    | O    | O    | O    | X    |
| E:first-child         | 첫 번째 자식 요소가 E라면 선택                       | O    | O    | O    | O    | O    | O    | O    | X    |
| E:lang(fr)            | HTML lang 속성의 값이 ‘fr’로 지정된 E를 선택         | O    | O    | O    | O    | O    | O    | X    | X    |
| E::before             | E 요소 전에 생성된 요소 선택                        | O    | O    | O    | O    | O    | O    | X    | X    |
| E::after              | E 요소 후에 생성된 요소 선택                        | O    | O    | O    | O    | O    | O    | X    | X    |
| E>F                   | E 요소의 자식인 F 요소 선택                        | O    | O    | O    | O    | O    | O    | O    | X    |
| E+F                   | E 요소를 뒤의 F 요소 선택                         | O    | O    | O    | O    | O    | O    | O    | X    |
| E[foo^=”bar”]         | ‘foo’ 속성의 값이 ‘bar’로 정확하게 시작하는 요소 선택      | O    | O    | O    | O    | O    | O    | O    | X    |
| E[foo$=”bar”]         | ‘foo’ 속성의 값이 ‘bar’로 정확하게 끝나는 요소 선택       | O    | O    | O    | O    | O    | O    | O    | X    |
| E[foo*=”bar”]         | ‘foo’ 속성의 값에 ‘bar’를 포함하는 요소 선택           | O    | O    | O    | O    | O    | O    | O    | X    |
| E:root                | 문서의 최상위 루트 요소 선택                         | O    | O    | O    | O    | O    | X    | X    | X    |
| E:nth-child(n)        | 그 부모의 n번째 자식이 앞으로부터 지정된 순서와 일치하는 E 라면 선택 | O    | O    | O    | O    | O    | X    | X    | X    |
| E:nth-last-child(n)   | n번째 자식이 뒤로부터 지정된 순서와 일치하는 요소가 E 라면 선택    | O    | O    | O    | O    | O    | X    | X    | X    |
| E:nth-of-type(n)      | E 요소 중 앞으로부터 순서가 일치하는 n번째 E 요소 선택        | O    | O    | O    | O    | O    | X    | X    | X    |
| E:nth-last-of-type(n) | E 요소 중 끝으로부터 순서가 일치하는 n번째 E 요소 선택        | O    | O    | O    | O    | O    | X    | X    | X    |
| E:last-child          | E 요소 중 마지막 자식이라면 E 선택                    | O    | O    | O    | O    | O    | X    | X    | X    |
| E:first-of-type       | E 요소 중 첫번째 E 선택                          | O    | O    | O    | O    | O    | X    | X    | X    |
| E:last-of-type        | E 요소 중 마지막 E 선택                          | O    | O    | O    | O    | O    | X    | X    | X    |
| E:only-child          | E 요소가 유일한 자식이면 선택                        | O    | O    | O    | O    | O    | X    | X    | X    |
| E:only-of-type        | E 요소가 같은 타입이면 선택                         | O    | O    | O    | O    | O    | X    | X    | X    |
| E:empty               | 텍스트 및 공백을 포함하여 빈 자식을 가진 E를 선택            | O    | O    | O    | O    | O    | X    | X    | X    |
| E:target              | E의 URI의 대상이 되면 선택                        | O    | O    | O    | O    | O    | X    | X    | X    |
| E:enabled             | 활성화된 폼 컨트롤 E요소 선택                        | O    | O    | O    | O    | O    | X    | X    | X    |
| E:disabled            | 비활성화된 폼 컨트롤 E요소 선택                       | O    | O    | O    | O    | O    | X    | X    | X    |
| E:checked             | 선택된 폼 컨트롤(라디오버튼,체크박스)을 선택                | O    | O    | O    | O    | O    | X    | X    | X    |
| E:not(s)              | s가 아닌 E 요소 선택                            | O    | O    | O    | O    | O    | X    | X    | X    |
| E~F                   | E 요소가 앞에 존재하면 F를 선택                      | O    | O    | O    | O    | O    | O    | O    | X    |