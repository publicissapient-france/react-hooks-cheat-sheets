## useRef
*useRef can just be used as a common React ref :*

```jsx
import { useRef } from "react";

function TextInput() {
  const inputRef = useRef(null);
  const onBtnClick = () => inputRef.current.focus();

  return (
    <>
      <input ref={ref} />
      <button onClick={onBtnClick}>Focus the text input</button>
    </>
  )
}
```

*But it also allows you to just hold a mutable value through any render. Also, mutating the value of ref.current will not cause any render*
