## **virtual**

**virtual** keyword helps us to determine that the class member can be overridden in a derived class.

If the member is not virtual, the member hiding will be performed, which usually is undesired. 
To explicitly show that method hiding is intentional, we use **new** keyword.

- **abstract** methods are **virtual**
- **virtual** methods do not need to be overridden, but **abstract** methods must be overridden.

## **override**

**override** keyword determines that the certain member overrides member with the same signature in the base class. 
Only **virtual** members can be overridden.

## **new**

**new** keyword can be used to mark the member in the derived class. It is used to demonstrate that the method hiding was intended.

It is not necessary to use **new** for hiding the member, but if **new** is not used the compiler will warn the developer.