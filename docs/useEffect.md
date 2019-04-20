### Class way

```jsx
class FriendStatus extends React.Component {

 state = { isOnline: null };

 componentDidMount() {
   ChatAPI.subscribeToFriendStatus(
     this.props.friend.id,
     this.handleStatusChange
   );
 }
 componentWillUnmount() {
   ChatAPI.unsubscribeFromFriendStatus(
     this.props.friend.id,
     this.handleStatusChange
   );
 }
 handleStatusChange = status => {
   this.setState({
     isOnline: status.isOnline
   });
 }
 render() {
   if (this.state.isOnline === null) {
     return 'Loading...';
   }
   return this.state.isOnline ? 'Online' : 'Offline';
 }
}
```

### Hooks way

```jsx
import { useState, useEffect } from 'react';

function FriendStatus(props) {
 const [isOnline, setIsOnline] = useState(null); // Store friend's online status

 const handleStatusChange = (status) => setIsOnline(status.isOnline);

 useEffect(
    () => {
      // Update status when it changes
      ChatAPI.subscribeToFriendStatus(
        props.friend.id, 
        handleStatusChange
      );

     // Stop listening to status changes every time we cleanup 
     return function cleanup() {
       ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
     };
   },
   [props.friend.id] // Cleanup when friend id changes or when we "unmount"
 );

 if (isOnline === null) {
   return 'Loading...';
 }
 return isOnline ? 'Online' : 'Offline';
}
```