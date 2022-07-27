## Attributes

Attributes are a special kind of classes, by which we can set metadata to the other types, methods, parameters or properties.
The naming convention for attributes is to add suffix "Attribute". For setting metadata using a certain attribute we do not need to include this suffix.

We can get metadata using reflections.

Attributes can be used for validation, serialization or binding with HTTP verbs.

We can define a custom attribute, by creating a class that inherits from a "Attribute" base class.

To apply the attribute we use square brackets [] just above the member or a class that we want to decorate.

We can limit the attribute usage, for instance to properties, by using the "AttributeUsage" attribute. Adding additional flag "AllowMultiple" results
in having the possibility to apply one attribute multiple times (for example in ASP.NET Core we can do it for binding to multiple endpoints).