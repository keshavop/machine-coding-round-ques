# 1. Create a countdown timer in ReactJS that goes from 60 to 1

```javascript
import React, { useState, useEffect } from 'react';

function CountdownTimer() {
  const [seconds, setSeconds] = useState(60);

  useEffect(() => {
    const interval = setInterval(() => {
      if (seconds > 1) {
        setSeconds(seconds - 1);
      } else {
        clearInterval(interval);
      }
    }, 1000);

    return () => clearInterval(interval);
  }, [seconds]);

  return (
    <div>
      <h1>Countdown Timer: {seconds}</h1>
    </div>
  );
}

export default CountdownTimer;
```

# 2. Create a countdown timer in ReactJS that goes from 60 to 1 
- add pause and reset buttons to your countdown timer in React, you can modify the previous example by adding two buttons and handling their click events.

```javascript
import React, { useState, useEffect } from 'react';

function CountdownTimer() {
  const [seconds, setSeconds] = useState(60);
  const [isPaused, setIsPaused] = useState(false);

  useEffect(() => {
    let interval;

    if (!isPaused && seconds > 1) {
      interval = setInterval(() => {
        setSeconds(seconds - 1);
      }, 1000);
    }

    return () => clearInterval(interval);
  }, [seconds, isPaused]);

  const handlePauseClick = () => {
    setIsPaused(!isPaused);
  };

  const handleResetClick = () => {
    setIsPaused(false);
    setSeconds(60);
  };

  return (
    <div>
      <h1>Countdown Timer: {seconds}</h1>
      <button onClick={handlePauseClick}>{isPaused ? 'Resume' : 'Pause'}</button>
      <button onClick={handleResetClick}>Reset</button>
    </div>
  );
}

export default CountdownTimer;
```

# 3. Made 4 box div containing a title and description and map through an array of objects and render it.
```javascript
import React from "react";

const Box = ({ title, text }) => {
  return (
    <div className="box">
      <h3>{title}</h3>
      <p>{text}</p>
    </div>
  );
};

const RowOfBoxes = ({ boxes }) => {
  return (
    <div className="row-of-boxes">
      {boxes.map((box) => (
        <Box key={box.id} title={box.title} text={box.text} />
      ))}
    </div>
  );
};

const App = () => {
  const boxes = [
    { id: 1, title: "Title 1", text: "Lorem Ipsum is simply dummy text of the printing and typesetting industry." },
    { id: 2, title: "Title 2", text: "Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book." },
    { id: 3, title: "Title 3", text: "It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged." },
    { id: 4, title: "Title 4", text: "It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker which included versions of Lorem Ipsum." },
  ];

  return (
    <div>
      <RowOfBoxes boxes={boxes} />
    </div>
  );
};

export default App;
```
