---
title: "fetch와 axios"
excerpt: "React에서 api 통신하기"

categories:
  - React
tags:
  - [React]

permalink: /React/20250620/fetch&axios

toc: true
toc_sticky: true

date: 2025-06-20
last_modified_at: 2025-06-20
---

### fetch
```js
const fetchPosts = async () => {
	try {
		const response = await fetch(`http://`);
		
		const data : {queries: string[]} = await response.json();
		return data.queries
		// 또는
		const data = await response.json();
		return data // 사용시 const {queries, total} = await fetchPosts()
	} catch(error) {
		console.error("에러발생: ", error);
		throw error;
	};
}
```
<br><br>

### fetch - http 메서드
```js
const getPosts = async () => {
	try {
		const response = await fetch(`http://`, {
			method: "POST", // "GET", "PUT", "DELETE"
			headers: {
				"Content-Type": "application/json",
			},
			body: JSON.stringify({
		    name: "Alice",
		    age: 25,
		  }),
		}),
		
		if (!response.ok) throw new Error("fetch 오류");
		
		const data = await response.json();
		return data;
	} catch(e) {
		console.error("에러발생: ", error);
		throw error;
	}
}
```
<br><br>

### axios 사용
src/api/axiosInstance.ts
```js
import axios from "axios";

export const axiosInstance = axios.create({
	baseURL: ``,
	headers: {
		accept: "application/json",
		Authorization: "",
	}
})
```
<br>

사용하려는 파일
```js
const [posts, setPosts] = useState([]);
const [error, setError] = useState("");

const fetchPost = async () => {
	try {
		const {data} = await axiosInstance.get("/posts");
		setPosts(data);
	} catch(e) {
		setError(e instanceof Error ? e.message : "Unknown Error");
	}
}

useEffect(() => {
	startTransition(async () => {
		await fetchPost();
	});
}, [])

return (
	<>
		<pre>{JSON.stringify(posts, null, 2)}</pre>
	</>
)
```
<br><br>

### axios - http 메서드
```js
// post - 등록, put - 전체 데이터 업데이트, patch - 일부분 업데이트, delete - 삭제
const postHandler = async () => {
	try {
		const { data } = await axiosInstance.post("/posts", {
			id: "4",
			title: "anna",
			views: 10,
		});
		console.log(data);
	} catch (e) {
		console.log(e instanceof Error && e.message);
	}
};

const deleteHandler = async () => {
	try {
		const { data } = await axiosInstance.delete("/posts/5");
		console.log(data);
	} catch (e) {
		console.log(e instanceof Error && e.message);
	}
};
```
<br><br>

