
## Why?

HTML,CSS로는 정적인 웹사이트를 만들 수 있을뿐이다.

JavaScript로 HTML의 제어를 통해서, 웹사이트를 보다 인터랙티브하게 변경할수 있다.

HTML을 JavaScript제어하기 위해서는 DOM(document object model) API를 사용할 수 있다.

또한 이벤트를 통한 프로그래밍도 이해해야 한다.


## 학습 목표

- DOM제어를 할 수 있다.
- node를 탐색 할 줄 안다.
- node를 찾을 수 있다.
- node의 구조를 변경(추가,삭제등)할 수 있다.

## DOM API 알아보기 미션

### 조심할 것

- blank node
- lastChild, lastElementChild

### 연산비용

- 트리구조가 자주 바뀔 때. 재배치 비용이 크다.
- dom 탐색이 빈번해도 비용이 크다.

### 탐색 할 때 범위를 줄일 것

- 더 작은 범위를 노드로 변수에 저장해서 탐색을 시작하자
- `dom 캐싱`이라는 키워드를 기억하자

### JS 제어

- inline style 속성을 추가하기도 하지만, 추후 파악하기 힘들기 때문에
- class 로 추상화해서 쓴다(목적은 가독성)
- 퍼포먼스는 inline 이 좋지만, JS 코드가 더러워짐

### JQuery 를 덜 쓰게 된 이유

- 요소 추가를 위해 함수 4개를 사용해서 만들었던 시절이 있다.
```html
<html>
  <head>
    <script>
       // run this function when the document is loaded
       window.onload = function() {

         // create a couple of elements in an otherwise empty HTML page
         var heading = document.createElement("h1");
         var heading_text = document.createTextNode("Big Head!");
         heading.appendChild(heading_text);
         document.body.appendChild(heading);
      }
    </script>
  </head>
  <body>
  </body>
</html>
```

- 그런데 이제 호환성 이슈가 줄었다.

- map, each 같은 것이 나왔다.

- Native 가 더 좋은 API를 제공하기 시작했다.

- 돔 조작이 더 편한 리엑트 JSX 같은 것들이 나왔다.

- 그래서 Jquery 의 사용 필요성이 적어졌다.

### Position

- 어렵다, 어떻게 값을 가져오고 처리할 것인가?
- 각 엘리먼트의 값
- 뷰포트의 높이값
- 스크롤이 있을때의 높이값

### Prototype 을 생각하면서 DOM 조작하자

- 각 계층별 정의되어 있는 메소드를 생각하자
- EventTarget
- Node
- Element
- HtmlElement

### JS DOM 조작할 때 브라우저는?

- 최적화를 한다. 최종적으로 계산한 결과가 바뀌지 않는다면 reflow, repaint에 반영하지 않음

## 미션 DOM API 둘러보기

### DOM Document

- activeElement : 포커스 된 요소를 반환

- adoptNode: 선택된 요소를 pop() 느낌

- importNode: adoptNode 와는 다르게 오리지널을 삭제하지 않고 복사만 함

- createDocumentFragment() : 

  공식문서 링크

  - fragment 객체를 통해 appendchild 하면 reflow 발생하지 않음

- createElement

- createTextNode

- creatEvent: 이벤트 시뮬레이션시에 활용. dispatch 와 함께 사용

- nomalize: 빈 텍스트 노드를 삭제하는 메소드

### Element

- accessKey : keyboard 접근을 위한 프로퍼티 설정
- appendChild
- childNodes : 공백 TextNode 포함
- children : 공백 TextNode 제외
- classList.add("class name")
- className = "mystyle";
- [clinet  vs offset](https://stackoverflow.com/questions/21064101/understanding-offsetwidth-clientwidth-scrollwidth-and-height-respectively) vs scrooll 개념

- cloneNode() : 노드를 카피함
- firstChild vs firstElementChild
- getAttribute()
- getAttributNode("class")
- hasAttribute("attribute name") : 특정 attribute 가 있는지 확인
- hasAttribute()
- setAttribute()
- setAttributeNode()
- tagName
- textContent
- previousElementSibling
- nextElementSibling
- parentNode, parentElement
- innerHTML
- innerText

### dom 추가

- insertAdjacentElement
- insertAdjacentHTML
- insertAdjacentText
- insertBefore

>  ## 참고 
> - 코드스쿼드 스텝 11
> - w3school 