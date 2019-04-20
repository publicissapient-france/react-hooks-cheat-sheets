```javascript
import { useState, useRef, useCallback, useEffect } from "React"; 

// let's hide the complexity of listening to hover changes
function useHover() {
  const [value, setValue] = useState(false); // store the hovered state
  const ref = useRef(null); // expose a ref to listen to

  // memoize function calls
  const handleMouseOver = useCallback(() => setValue(true), []);
  const handleMouseOut = useCallback(() => setValue(false), []);

  // add listeners inside an effect,
  // and listen for ref changes to apply the effect again
  useEffect(() => {
    const node = ref.current;
    if (node) {
      node.addEventListener("mouseover", handleMouseOver);
      node.addEventListener("mouseout", handleMouseOut);

      return () => {
        node.removeEventListener("mouseover", handleMouseOver);
        node.removeEventListener("mouseout", handleMouseOut);
      };
    }
  }, [ref.current]);

  // return the pair of the exposed ref and it's hovered state
  return [ref, value];
}
```

```jsx
const HoverableComponent = () => {
  const [ref, isHovered] = useHover();
  return (
    <span style={{ color: isHovered ? "blue" : "red" }} ref={ref}>
      Hello React hooks !
    </span>
  );
};
```