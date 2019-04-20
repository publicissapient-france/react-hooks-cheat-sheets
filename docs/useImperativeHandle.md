## useImperativeHandle
*Allows you to customize the exposed interface of a component when using a ref. The following component will automatically focus the child input when mounted :*

```jsx
function ChildInput(props, ref) {
  const inputRef = useRef(null);
  useImperativeHandle(ref, () => inputRef.current);

  return <input type="text" name="child input" ref={inputRef} />;
}

function Parent() {
  const inputRef = useRef(null);

  useEffect(() => {
    inputRef.current.focus();
  }, []);

  return (
    <div>
      <ChildInput ref={inputRef} />
    </div>
  );
}
```