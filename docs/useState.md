### Class way

```JSX
const initialCount = 0;

class Counter extends Component {
  constructor(props) {
    super(props);
    this.state = { count: initialCount };
  }

  render() {
    return (
      <div>
        <p>You clicked {this.state.count} times</p>
        <button
            onClick={() => this.setState(({count}) => ({ count: count + 1 }))}
        >
          Click me
        </button>
      </div>
    );
  }
}
```

### Hook way

```JSX
import { useState } from "React";

const initialCount = 0;
function Counter() {
  const [count, setCount] = useState(initialCount);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button
        onClick={() => setCount((c) => c + 1)}
      >
        Click me
      </button>
    </div>
  );
}

```
