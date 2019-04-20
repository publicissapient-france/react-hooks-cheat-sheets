# What hooks can do for you

## Manage state

### [useState](/docs/useState.md)

```javascript
const [count, setCount] = useState(initialCount);
```

### useReducer

```javascript
const [state, dispatch] = useReducer(
    reducer, 
    initialState, 
    initialDispatch
);
```

## Handling side effects

### useEffect

```javascript
useEffect(() => {
  applyEffect(dependencies);
  return () => cleanupEffect();
}, [dependencies]);
```

### useLayoutEffect

```javascript
useLayoutEffect(() => {
  applyBlockingEffectAfterRender(dependencies);
  return cleanupEffect();
}, [dependencies]);
```

## Using the Context API

### useContext
```javascript
const ThemeContext = React.createContext();
const contextValue = useContext(ThemeContext);
```

## Memoize everything

### useMemo
```javascript
const memoizedValue = useMemo(
    expensiveFn(dependencies), 
    [dependencies]
);
```

### useCallback
```javascript
const memoizedCallback = useCallback(
    () => expensiveFn(dependencies), 
    [dependencies]
);
```

## Good ol' refs

### useRef
```javascript
const ref = useRef();
```

### useImperativeHandle

```javascript
useImperativeHandle(
    ref, 
    createHandle, 
    [dependencies]
)
```

## Reusability

###Extract reusable behaviour into custom hooks