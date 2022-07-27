## Access modifiers

Keywords used to determine the certain type of type member accessibility.

In C# we have the following access modifiers for types:
- private
- internal
- public

For the type members:
- private
- protected
- internal
- protected internal
- public
- private protected

Default access modifier for classes is **internal**.  
Default access modifier for class members is **private**.  
Default access modifier for structs is **internal**.  
Default access modifier for struct members is **private**.  

## private

For types:
type is accessible only in the supertype.

For members:
member is accessible only in the current type.

## public 

Type or type member is accessible for all other modules.

## protected

For member:
member is accessible only for the current type and the types that derive from current type.

## internal 

For types and type members:
it is like public, but only to types in the same assembly.

## protected internal

For members:
it specifies that access is limited to the current assembly or types derived from the containing class.

**protected internal** modifier means *protected OR internal*.

## private protected

For members:
it is used to specify that the access is limited to the containing class or types derived from the containing class within the current assembly.

**private protected** means *protected AND internal*.