# Create a countdown timer in ReactJS that goes from 60 to 1

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

# Create a countdown timer in ReactJS that goes from 60 to 1 
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
