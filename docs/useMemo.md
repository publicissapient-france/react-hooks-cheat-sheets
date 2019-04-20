## useMemo

```jsx
function RandomColoredLetter(props) {
  const [color, setColor] = useState('#fff')
  const [letter, setLetter] = useState('a')
  const handleColorChange = useMemo(() => () => setColor(randomColor()), []);
  const handleLetterChange = useMemo(() => () => setLetter(randomColor()), []);
  return (
    <div>
      <ColorPicker handleChange={handleColorChange} color={color} />
      <LetterPicker handleChange={handleLetterChange} letter={letter} />
      <hr />
      <h1 style={{color}}>{letter}</h1>
    </div>
  )
}
```