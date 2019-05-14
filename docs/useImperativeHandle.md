## useImperativeHandle
*Allows you to customize the exposed interface of a component when using a ref. The following component will automatically focus the child input when mounted :*

```jsx
function TextInput(props, ref) {
  const inputRef = useRef(null);
  const onBtnClick = () => inputRef.current.focus();

  useImperativeHandle(ref, () => ({
    focusInput: () => inputRef.current.focus();
  });

  return (
    <>
      <input ref={inputRef} />
      <button onClick={onBtnClick}>Focus the text input</button>
    </>
  )
}

const TextInputWithRef = React.forwardRef(TextInput);

function Parent() {
  const ref = useRef(null);

  useEffect(() => {
    ref.focusInput();
  }, []);

  return (
    <div>
      <TextInputWithRef ref={ref} />
    </div>
  );
}
```