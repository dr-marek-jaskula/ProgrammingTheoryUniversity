## Delegate

The basic understanding is that the delegate is a pointer to a function, but in a safe way, not like in a C++.

The term "delegates" was used to outline the fact that this approach was designed to send a class member to 
ensure communication with other classes, especially when the long-running processes are being executed or to 
communicate between different threads.

## Events

Events provide encapsulation over delegates. This approach ensured that the delegates are not modified by anyone.
Events change the delegate to the publisher-subscriber model.

Events in C# are rarely use these days.