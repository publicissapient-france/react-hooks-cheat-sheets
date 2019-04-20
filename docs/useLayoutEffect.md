## useLayoutEffect
*Almost the same as useEffect, but fires synchronously after the render phase. Use this to safely read from or write to the DOM*

```jsx
import { useRef, useLayoutEffect } from "React";

function ColoredComponent({color}) {
  const ref = useRef();

  useLayoutEffect(() => {
    const refColor = ref.current.style.color;
    console.log(`${refColor} will always be the same as ${color}`);
    ref.current.style.color = "rgba(255,0,0)";
  }, [color]);

  useEffect(() => {
    const refColor = ref.current.style.color;
    console.log(
      `but ${refColor} can be different from ${color} if you play with the DOM`
    );
  }, [color]);

  return (
    <div ref={ref} style={{ color: color }}>
      Hello React hooks !
    </div>
  );
}
```

```jsx
<Component color={"rgb(42, 13, 37)"} />
// rgb(42, 13, 37) will always be the same as rgb(42, 13, 37)
// but rgb(255, 0, 0) can be different from rgb(42, 13, 37) if you play with the DOM
```