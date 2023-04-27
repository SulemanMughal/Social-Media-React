#   ES6 Features

**JSX Styling**

```


import React from 'react';
function Component() {
  return (
    <div>
      <h1>Hello, world!</h1>
      <p>This is some text.</p>
    </div>
  );
}


```


```

import React from 'react';
function Component({ name }) {
  return (
    <div>
      <h1>Hello, {name}!</h1>
      <p>This is some text.</p>
    </div>
  );

```


**Props versus states**

```

import React from 'react';
function ParentComponent() {
  return (
    <ChildComponent
      name="John Doe"
      age={25}
    />
  );
}
function ChildComponent({ name, age }) {
  return (
    <p>
      My name is {name} and I am {age} years old.
    </p>
  );
}

```


```
import React, { useState } from 'react';
function Counter() {
  // Use useState to manage the state of the counter
  const [count, setCount] = useState(0);
  // Function to increment the counter
  function handleIncrement() {
    setCount(count + 1);
  }
  return (
    <div>
      <p>The counter is at {count}.</p>
      <button onClick={handleIncrement}>Increment</button>
    </div>
  );
}

```


**The Context API**


```

// Create a context for sharing data
const Context = React.createContext();
function App() {
  // Set some initial data in the context
  const data = {
    message: 'Hello, world!'
  };
  return (
    // Provide the data to the components inside the
    // Provider
    <Context.Provider value={data}>
      <Component />
    </Context.Provider>
  );
}
function Component() {
  // Use the useContext Hook to access the data in the
  // context
  const context = React.useContext(Context);
  return (
    <p>{context.message}</p>
  );
}

```


**useMemo**


```

import React, { useMemo } from 'react';
function Component({ data }) {
  // Use useMemo to memoize the expensive calculation
  const processedData = useMemo(() => {
    // Do some expensive calculation with the data
    return expensiveCalculation(data);
  }, [data]);
  return (
    <div>
      {/* Use the processed data in the component */}
      <p>{processedData.message}</p>
    </div>
  );
}

```


**Handling forms – controlled components and uncontrolled components**

```

import React, { useState } from 'react';
function Form() {
  // Use useState to manage the state of the input field
  const [inputValue, setInputValue] = useState('');
  // Function to handle changes to the input field
  function handleChange(event) {
    setInputValue(event.target.value);
  }
  return (
    <form>
      <label htmlFor="name">Name:</label>
      <input
        type="text"
        id="name"
        value={inputValue}
        onChange={handleChange}
      />
    </form>
  );
}

```


```

import React from 'react';
function Form() {
  // Use a ref to manage the state of the input field
  const inputRef = React.useRef();
  // Function to handle the form submission
  function handleSubmit(event) {
    event.preventDefault();
    // Do something with the input value here
    // For example, you might send the input value to an
    // API or save it to the database
    sendInputValue(inputRef.current.value);
    // Clear the input after submitting
    inputRef.current.value = '';
  }
  return (
    <form onSubmit={handleSubmit}>
      <label htmlFor="name">Name:</label>
      <input
        type="text"
        id="name"
        defaultValue=""
        ref={inputRef}
      />
    </form>
  );
}

```