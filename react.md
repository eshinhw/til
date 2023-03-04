# React.js

## How to initialize React Project

`npx create-react-app dirName` : create a new react app project in `dirName`

## Basics of React.js

- `App.js` 에서 짜여진 JSX 코드들을 `index.js` 가 `index.html` 로 집어넣어주는 관계.

- JSX Syntax
    - Use `className` instead of `class` inside HTML tags
    - Use  `<h4>{ varName }</h4>` for data binding
    - Inline Style
        - HTML: `style="color: red"`
        - JSX: `style={ { color: 'red', fontSize: '16px' } }` with camelCase
- Disable YELLOW Warnings!
    - place `/* eslint-disable */` at the top of the file

## What is `useState`?

- `useState` 로 변수 선언시 값이 변할때마다 자동으로 업데이트 되어짐.
- 자주 바뀌어야하는 변수들은 `useState` 로 선언하면 됨.
- 일반 변수는 값이 변경되면 html 안에서 업데이트가 되지 않음. 하지만 `useState` 경우에는 변경시 html 전체가 자동으로 리렌더링 됨.
- array/object 데이터를 다룰 때는 원본을 보전하는 것이 좋음.
- 기존 스테이트와 신규 스테이트가 같을 경우 변경이 안됨.
- array variable 은 포인터 개념. reference data type
- 변수 2개의 포인터가 같은곳을 가르키면 비교시 true.

## How to Create a Component

1. create a function
2. include html codes in return()
3. <funcName />

## What is the difference between `()` and `{}`

The following two statements are identical. For single statements, `return` isn't needed. However, We need `return` keyword if we use curly braces.

```
blogs.map(blog => (<h1> {b.title}))
blogs.map(blog => {return (<h1> {b.title})})
```

## What are Props in React?

Inside `Home.js`, we have the following.

```javascript
const Home = () => {
  const [blogs, setBlogs] = useState([
    { title: "My new website", body: "body1", author: "mario", id: 1 },
    { title: "Welcome!", body: "body2", author: "suzuki", id: 2 },
    { title: "Hello", body: "body3", author: "mario", id: 3 },
  ]);

  const handleDelete = (id) => {
    console.log("delete a blog with id");
    const newBlogs = blogs.filter((blog) => blog.id != id);
    setBlogs(newBlogs);
  }

  return (
    <div className="home">
      // props are blogs, title and handleDelete.
      <BlogList blogs= {blogs} title="All Blogs" handleDelete={handleDelete}>
    </div>
  );
};

export default Home;
```

Inside `BlogList.js`, we have the following.

```javascript
// We have to access props provided in Home.js as input parameters.
// There are two ways of accessing props.
// 1) const BlogList = (props) => {} Then props.blogs, props.title and props.handleDelete
// 2) const BlogList = ({ blogs, title, handleDelete }) => {} Then blogs = props.blogs, title = props.title and handleDelete = props.handleDelete
const BlogList = (props) => {
  return (
    <div className="blog-list">
      <h2>{ title }</h2>
      // Why do we need key value?
      {blogs.map((blog) => (
        <div className="blog-preview" key={blog.id}>
          <h2>{ blog.title }</h2>
          <p>Written by { blog.author }</p>
          <button>Click Me</button>
        </div>
      ))}
    </div>
  )
}

export default BlogList;
```

## What is `useEffect`?

`useEffect` runs a function every render of the component.

```
import { useEffect } from 'react';

// doesn't return anything. We pass a function as an argument. 
// Always run once when initial load is occurred. 

useEffect();

useEffect(() => {
  console.log("use effect ran");
  console.log(name);
}, [name]); // Dependencies in useEffect => only runs when name var is changed.
```

## How to apply Conditional Syntax in React?

If logic is true, A is executed. Otherwise, B is executed.

```javascript
{logic ? (A) : (B)}
```

 




