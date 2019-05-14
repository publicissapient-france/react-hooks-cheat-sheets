# React hooks Cheat Sheets

## What hooks can do for you

### Manage state

#### [useState](/docs/useState.md)

```javascript
const [count, setCount] = useState(initialCount);
```

#### [useReducer](/docs/useReducer.md)

```javascript
const [state, dispatch] = useReducer(
  reducer, 
  initialState, 
  initialDispatch
);
```

### Handle side effects

#### [useEffect](/docs/useEffect.md)

```javascript
useEffect(() => {
  applyEffect(dependencies);
  return () => cleanupEffect();
}, [dependencies]);
```

#### [useLayoutEffect](/docs/useLayoutEffect.md)

```javascript
useLayoutEffect(() => {
  applyBlockingEffect(dependencies);
  return cleanupEffect();
}, [dependencies]);
```

### Use the Context API

#### [useContext](/docs/useContext.md)

```javascript
const ThemeContext = React.createContext();
const contextValue = useContext(ThemeContext);
```

### Memoize everything

#### [useMemo](/docs/useMemo.md)

```javascript
const memoizedValue = useMemo(
  () => expensiveFn(dependencies),
  [dependencies]  
);
```

#### [useCallback](/docs/useCallback.md)

```javascript
const memoizedCallback = useCallback(
  expensiveFn(dependencies),
  [dependencies]
);
```

### Use refs

#### [useRef](/docs/useRef.md)

```javascript
const ref = useRef();
```

#### [useImperativeHandle](/docs/useImperativeHandle.md)

```javascript
useImperativeHandle(
  ref,
  createHandle,
  [dependencies]
)
```

### Reusability

#### [Extract reusable behaviour into custom hooks](/docs/customHooks.md)
