---
title: "React Router"
excerpt: "data mode React Router"

categories:
  - React
tags:
  - [React]

permalink: /React/20250620/react-router

toc: true
toc_sticky: true

date: 2025-06-20
last_modified_at: 2025-06-20
---

`npm i react-router` 로 설치 <br> <br>

src/routes/index.tsx <br>
src/routes/pages/About.tsx <br>
src/routes/pages/Home.tsx <br>
src/routes/index.tsx <br>
<br>

```jsx
import {createBrowserRouter, RouterProvider} from "react-router";

const router = createBrowserRouter([
  {
    path: "/",
    element: <Home />,
  },
  {
    path: "/about",
    element: <About />,
  },
]);

export default function Router() {
	return (
		<>
			<RouterProvider router={router}>
		</>
	)
}
```
<br> <br>

```
{
  path: "/",
  element: <Home />,
},
```
<br>
이게 `라우트 객체` <br>

라우트 객체들이 묶여서 전체적인 역할을 하게 해주는 router 변수를 `라우터 인스턴스 객체`라고 한다. <br><br>

컴포넌트를 전달할 때는 element 대신에 `Component: Home`, 이렇게 전달할 수도 있다. <br>
Home은 auto import 필요함.<br><br>

element는 jsx도 전달할 수 있다.<br><br>
<br>

### 중첩 라우트
중첩 시키고 싶을 때는 children속성으로 중첩한다.<br>
그리고 부모 컴포넌트에 가서 꼭 <Outlet>을 적용해줘야 한다. 그래야 Outlet 위치에 children에 지정한 컴포넌트가 보여진다.<br><br>

src/routes/index.tsx
```jsx
const router = createBrowserRouter([
  {
    path: "/",
    element: <Home />,
  },
  {
    path: "/dashboard",
    element: <Dashboard />,
    children: [
	    {
		    path: "", // index: true 라고 적어도 똑같음. (인덱스 라우트)
			  element: <DashBoardHome />
	    }
    ]
  },
]);
```
<br>

src/routes/pages/dashboard/Dashboard.tsx
```jsx
import {Outlet} from "react-router";

export default function Dashboard () {
	return (
		<>
			<h1>Dashboard</h1>
			<Outlet />
		</>
	)
}
```
<br>

인덱스 라우트는 children을 가질 수 없는데 인덱스 라우트가 아니면 또 children 중첩이 가능하다.<br>
children속성으로 중첩된 라우트의 path에는 `/`를 붙이지 않는다. <br><br>
<br>

### App 컴포넌트 지우기
main.tsx
```jsx
import { StrictMode } from "react";
import { createRoot } from "react-dom/client";
import "./css/index.css";
import Router from "./routes";

createRoot(document.getElementById("root")!).render(
  <StrictMode>
    <Router />
  </StrictMode>
);
```
<br><br>

### App 컴포넌트 지우지 않기
main.tsx
```jsx
import { StrictMode } from "react";
import { createRoot } from "react-dom/client";
import "./css/index.css";
import App from "./App.tsx";

createRoot(document.getElementById("root")!).render(
  <StrictMode>
    <App />
  </StrictMode>
);
```
<br>

App.tsx
```jsx
import Router from "./routes";

export default function App() {
  return (
    <>
      <Router />
    </>
  );
}
```
<br><br>

## layout 라우트
src/routes/pages/layouts/RootLayout.tsx
```jsx
import {Outlet} from "react-router";

export default function RootLayout() {
	return (
		<>
			<header></header>
			<Outlet />
			<footer></footer>
		</>
	)
}
```
<br>

src/routes/index.tsx
```jsx
import {createBrowserRouter, RouterProvider} from "react-router";

const router = createBrowserRouter([
	{
		element: <RootLayout />,
		children: [
			{
		    path: "/",
		    element: <Home />,
		  },
		  {
		    path: "/about",
		    element: <About />,
		  },
		]
	}
]);

export default function Router() {
	return (
		<>
			<RouterProvider router={router}>
		</>
	)
}
```
<br>

레이아웃은 얼마든지 중첩 가능.<br><br>
<br>

## 라우트 prefix
element는 없이 공통의 세그먼트만 추가하고 싶을 때<br>
```jsx
import {createBrowserRouter, RouterProvider} from "react-router";

const router = createBrowserRouter([
	{
		element: <RootLayout />,
		children: [
			{
		    path: "/",
		    element: <Home />,
		  },
		  {
		    path: "/about",
		    element: <About />,
		  },
		  {
			  path: "/group", 
			  children: [
				  {
				    path: "dashboard", // <- /없어야 됨
				    element: <Dashboard />,
				    children: [
					    {
						    path: "",
							  element: <DashBoardHome />
					    }
				    ]
				  },
			  ]
		  }

		]
	}
]);

export default function Router() {
	return (
		<>
			<RouterProvider router={router}>
		</>
	)
}
```
<br><br><br>
