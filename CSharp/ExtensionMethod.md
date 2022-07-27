## Extension method

Extension method is a method that allows us to add a functionality to the existing type, from the outside of its definition.

For instance, we can extend the "string" type, to be able to call a new method directly on a string variable. 
Let us notice, that for some types the inheritance is impossible (they are sealed), so the functionality cannot be extended using inheritance.

In other to create an extension method we need to:
- Create a static class (non nested, non generic)
- Create a public static method in this class
- The first parameter of this method must be a variable of type we want to extend and preceded by **this** keyword