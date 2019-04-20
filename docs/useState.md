### Classic way

```JSX
const initialCount = 0;

class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: initialCount };
  }

  render() {
    return (
      <div>
        <p>You clicked {this.state.count} times</p>
        <button
            onClick={() => this.setState(({c}) => ({ count: c + 1 }))}
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
function Counter() {
  const [count, setCount] = useState(0);

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
