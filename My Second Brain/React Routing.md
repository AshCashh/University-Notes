---
aliases:
  - React Route
tags: [webdev]
Created: 2024-03-23T11:09:06+10:00
Modified: 2024-07-03T19:35:33+10:00
---
[[Routers & Routing|Routing]] is the process of redirecting a user to different pages based on their action or request. We can route from page to page in [[React]] using a popular library called `BrowserRouter`. In `BrowserRouter` each `Link` needs to have a corresponding `Route` to specify which page the user gets directed to.

In general we should have:
- Consistent URLs - the browser address window should update
- The back and forward buttons working normally
- Direct link access to a view - deep linking should work

React Router also provides to us a collection of utility hooks that we can use. Here are a few examples:
- `useParams`: Access path parameters
- `useSearchParam`: Access query string parameters
- `useNavigate`: Navigate to a page programatically without the need to include a link

# Example
```java
// index.js
import ReactDOM from "react-dom";
import { BrowserRouter, Routes, Route, Link } from "react-router";

const Home = () => {
  return (
    <div>
      <h1>Welcome to my Home Page</h1>
      <p>Keep on reading to learn more about React Routing</p>
    </div>
  );
};

const Blogs = () => {
  return (
    <div>
      <h1>My Blogs</h1>
      <p>Keep on reading to learn more about my blogs</p>
    </div>
  );
};

const App = () => {
  return (
    <BrowserRouter>
      <div className="App">
        <nav className="navBar">
          <Link to={"/"}>Home</Link>
          <Link to={"/blogs"}>Blogs</Link>
        </nav>

        <main>
          <Routes>
            <Route path="/" element={<Home />} />
            <Route path="/blogs" element={<Blogs />} />
          </Routes>
        </main>
      </div>
    </BrowserRouter>
  );
};

const rootElement = document.getElementById("root");
ReactDOM.render(<App />, rootElement);
```

```js
function App(){
	return(
		<BrowserRouter>
	
	
	)


}