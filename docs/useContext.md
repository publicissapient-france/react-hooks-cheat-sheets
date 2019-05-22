### Class way

```jsx
class Header extends React.Component {
  public render() {
    return (
      <AuthContext.Consumer>
        {({ handleLogin, isLoggedIn}) => (
          <ModalContext.Consumer>
            {({ isOpen, showModal, hideModal }) => (
              <NotificationContext.Consumer>
                {({ notification, notify }) => {
                  return (
                    ...
                  )
                }}
              </NotificationContext.Consumer>
            )}
          </ModalContext.Consumer>
        )}
      </AuthContext.Consumer>
    );
  }
}
```

### Hook way

```jsx
import { useContext } from 'react';

function Header() {

  const { handleLogin, isLoggedIn} = useContext(AuthContext); //
  const { isOpen, showModal, hideModal } = useContext(ModalContext);
  const { notification, notify } = useContext(NotificationContext);

  return ...
}

```

#### ⚠️ Use the created context, not the consumer ⚠️
```jsx
const Context = React.createContext(defaultValue);

// Wrong
const value = useContext(Context.Consumer);

// Right
const value = useContext(Context);
```
