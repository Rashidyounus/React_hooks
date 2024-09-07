# React_hooks
/// Use State
import logo from "./logo.svg";
import "./App.css";
import { useState } from "react";

function App() {
  const handlecolor = () => {
    setColor("blue");
  };
  // let color = "Red";

  //const [color, setColor] = useState("Red");
  console.log(useState("Red"));

  const [brand, setBrand] = useState("ferrari");
  const [model, setModel] = useState("Roma");
  const [year, setYear] = useState("2023");
  const [color, setColor] = useState("red");

  const [car, setCar] = useState({
    brand: "Ferrari",
    model: "Roma",
    year: "2023",
    color: "red",
  });

  const changeColor = () => {
    // setCar({ color: "blue" });

    setCar((car) => {
      return { ...car, color: "blue" };
    });
  };

  const [count, setCount] = useState(0);

  const Increment = () => {
    setCount((count) => count + 1);
  };
  return (
    <>
      <div>
        <h1>My favourite color is {color}</h1>
        <button onClick={handlecolor}>Blue</button>
      </div>

      <div>
        <h1>My {brand}</h1>
        <h2>
          It is a {color} {model} from {year}
        </h2>
      </div>
      <div>
        <h1>My {car.brand}</h1>
        <h2>
          It is a {car.color} {car.model} from {car.year}
        </h2>
        <button onClick={changeColor}>Blue</button>
      </div>
      <div>
        <h1>count :{count}</h1>
        <button onClick={Increment}>Increment</button>
      </div>
    </>
  );
}

export default App;



/// use Ref

import logo from "./logo.svg";
import "./App.css";
import { useEffect, useState } from "react";

function App() {
  const [count, setCount] = useState(0);
  const [counter, setCounter] = useState(0);
  const [name, setName] = useState("Rashid");

  // useEffect(() => {
  //   setTimeout(() => {
  //     setCount((count) => count + 1);
  //   }, 2000);
  // });

  useEffect(() => {
    console.log("Test---1");
  });

  useEffect(() => {
    console.log("Test---2");
  }, []);

  useEffect(() => {
    console.log("Test---3");
  }, [name]);

  return (
    <div>
      <h1>Use Effect</h1>
      <h2>Rendered {count} times!</h2>

      <br />

      <br />

      <h1>{counter}</h1>
      <h1>{name}</h1>
      <button
        onClick={() => {
          setCounter(counter - 1);
        }}
      >
        Decrement
      </button>

      <button
        onClick={() => {
          setCounter(counter + 1);
        }}
      >
        Increment
      </button>

      <button
        onClick={() => {
          setName("khan");
        }}
      >
        update
      </button>
    </div>
  );
}

export default App;

import logo from "./logo.svg";
import "./App.css";
import { useCallback, useMemo, useRef, useState } from "react";
import Header from "./Header";

function App() {
  /// Use Ref
  /* const inputElem = useRef();

  const btnClicked = () => {
    console.log(inputElem.current);
    // inputElem.current.style.background = "blue";
    const v = inputElem.current.value;
    console.log(v);

    inputElem.current.value = "";
  };
  return (
    <div className="App">
      <h1>Use Ref</h1>
      <input type="text" ref={inputElem} />
      <button onClick={btnClicked}>Click Here</button>
    </div>
  );

  */
  // use Memo
  /*
  const [number, setNumber] = useState(0);
  const [count, setCount] = useState(0);

  function cubeNumber(num) {
    console.log("Calculation done");
    return Math.pow(num, 3);
  }

  // const result = cubeNumber(number);
  const result = useMemo(() => {
    return cubeNumber(number);
  }, [number]);

  return (
    <>
      <input
        type="number"
        value={number}
        onChange={(e) => {
          setNumber(e.target.value);
        }}
      />
      <h1>Cube of the number: {result}</h1>

      <button
        onClick={() => {
          setCount(count + 1);
        }}
      >
        Counter++
      </button>
      <h1>Counter:{count}</h1>
    </>
  );
  */
  // useCallBack  hook

  const [count, setCount] = useState(0);

  // const newFn = () => {};

  const newFn = useCallback(() => {}, []);
  return (
    <>
      <Header newFn={newFn}></Header>
      <h1>{count}</h1>

      <button onClick={() => setCount((prev) => prev + 1)}>Click Here</button>
    </>
  );
}
export default App;



