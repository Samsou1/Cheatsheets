# React

## Create an app
```
npm create vite@latest app-name
cd app-name
npm install
npm run dev
```

## UseState

```
import { useState } from 'react'

const [example, setExample] = useState(defaultState)
```

When changing the state, it's important to change it via a function like
```
const [count, setCount] = useState(0)
const incrementCount = () => {setCount(prevCount => prevCount + 1)}
```
if not, there might be a problem as if you try to get the state value, you might get the unchanged value as it changes only when the component rerenders. By using a function, you get rid of such problems.


## UseEffect

```
import { useEffect } from 'react'

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `You clicked ${count} times`;
  });

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

## Router

```
import {
  BrowserRouter,
  Routes,
  Route,
} from 'react-router-dom';

const App = () => {
  return (
    <BrowserRouter>
      <main>
        <Navbar />
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/about" element={<About />} />
          <Route path="/documentation" element={<Documentation />} />
          <Route path="/works" element={<Work />} />
          <Route path="/works/:element" element={<Item />} />
        </Routes>
      </main>
    </BrowserRouter>
  );
}
```

## Link
```
import {Link} from 'react-router-dom';
const Work = () => {
  return (<div>
    <h1>Welcome on the works page. Please, select a category</h1>
    <Link to="/works/exercices">Exercices</Link>
    <Link to="/works/case_study">Case Study</Link>
    <Link to="/works/concret_case">Concret case</Link>
  </div>)
}
```

## CreateContext

Create a file with the context
```
import { createContext } from 'react';
const nightMode = createContext(false);
export default nightMode;
```

In App.jsx, import the const
```
import nightMode from './assets/nightMode';
function App() {
  const [nM, setNM] = useState(false);

  return (
    <div className="App">
      <nightMode.Provider value={{nM, toggleNM:() => {setNM(!nM)}}}>
        <Header />
        <Works />
        <Contact />
      </nightMode.Provider>
    </div>
  )
}
```

In the composant you want to display the value or change the value:
```
import nightMode from "../../assets/nightMode" //Import the createContext
```
In the same composant you can then access the Context value and change it:
```
const Header = () => {
  const night = useContext(nightMode);
  if(night.nM){
    console.log("Night mode on")
  }
  return (
    <div>
      <h1>Portfolio de John Doe</h1>
      <button onClick={night.toggleNM}>Night mode</button>
    </div>
  )
}
```

You can also destructure the context this way:
```
const Header = () => {
  const {nM, toggleNM} = useContext(nightMode);
  if(nM){
    console.log("Night mode on")
  }
  return (
    <div>
      <h1>Portfolio de John Doe</h1>
      <button onClick={toggleNM}>Night mode</button>
    </div>
  )
}
```

## Showdown

Import
```
import Showdown from 'showdown';
const converter = new Showdown.Converter();
```

Use
```
const markdown_string_to_convert = '# Hello world';
<div dangerouslySetInnerHTML={{__html: converter.makeHtml(markdown_string_to_convert)}}></div>
```

## Useparams()

Import
```
import {useParams} from 'react-router-dom';
```

Use in a component (be careful not to use it in a hook like Useeffect)
```
const items = useParams()
```