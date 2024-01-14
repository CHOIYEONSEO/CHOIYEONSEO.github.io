---
title: "[모청] html form과 구글폼 연동해서 스프레드시트에 데이터 저장"
excerpt: "첫번째 요구사항 2차"

categories:
  - Project
tags:
  - [Project, 모청, Project1]

permalink: /Project/20240114/

toc: true
toc_sticky: true

date: 2024-01-14
last_modified_at: 2024-01-14
---

[참고] <https://www.youtube.com/watch?v=eVvhNAnOf1A&t=745s> <br>
<https://do-first-dream-next.tistory.com/entry/%EB%B3%B4%ED%8E%B8%EC%A0%81%EC%9D%B4%EC%A7%80-%EC%95%8A%EC%9D%80-%EA%B0%9C%EB%B0%9C3-%EA%B5%AC%EA%B8%80-%EC%8A%A4%ED%94%84%EB%A0%88%EB%93%9C-%EC%8B%9C%ED%8A%B8%EB%A5%BC-DB%EC%B2%98%EB%9F%BC-%EC%9D%B4%EC%9A%A9%ED%95%B4%EB%B3%B4%EC%9E%90><br>

먼저 구글폼에서 html form으로 만든 항목들을 똑같이 추가한 설문지를 만든다.<br>
이때, input 태그가 text가 아닌 다른 태그였더라도(ie. input:radio, select) 상관없이 구글폼의 항목들은 모두 텍스트 항목으로 만든다.<br><br>

우측 상단의 보내기 버튼->링크복사를 통해 사람들에게 공유될 페이지로 이동한뒤, 개발자도구를 사용하여 form 태그의 action 속성값을 찾아 복사한뒤 html의 form 태그의 action 속성값으로 붙여넣기 해준다.<br>
html form 태그의 method 속성값은 post로, target 속성값은 구글폼이 성공적으로 제출되었다는 창이 새로운 탭으로 열리게 하고 싶으면 _blank로 해당 창에서 이동하게 하고 싶으면 _self로 적어준다. 안적으면 _self로 간주.<br><br>

다시 설문지를 만들던 페이지로 이동하여 우측 상단의 점세개 더보기->미리 채워진 링크 가져오기를 클릭한뒤, 구글폼 항목별 input태그의 name 값을 확인한다. 이 name값은 고유값으로 복사하여 html의 input태그의 name 속성값으로 붙여넣기 해주면 된다.<br><br>

--> 이렇게 html form과 구글폼 연동하여 스프레드시트에 데이터 저장하기 완료!
