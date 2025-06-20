---
title: "한글 두번 입력되는 오류 해결"
excerpt: "onKeyDown 버그"

categories:
  - React
tags:
  - [React]

permalink: /React/20250620/onKeyDown

toc: true
toc_sticky: true

date: 2025-06-20
last_modified_at: 2025-06-20
---

한글은 조합 문자라서 마지막 글자가 한번 더 입력되는 오류가 있다.<br>
방지하기 위해서는 isComposing을 확인해주면 된다.<br>
```js
value={search}
onChange={(e) => setSearch(e.target.value)}
onKeyDown={(e) ⇒ {
	if (e.key === "Enter" && e.nativeEvent.isComposing === false) {
		// 이안에 작성
	}
}}
```
