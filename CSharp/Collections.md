## Array

Array is a collection of items with specified datatype (it is strongly typed) and fixed size called *length*.

Nevertheless, we can resize the array by ".Resize()" method, but it is something that should be avoided.
The performance of Array is good because of being strongly typed (and fixed size).

The Array which has elements of type array is called jagged Array. 
The elements can be of different dimensions and sizes.

## ArrayList

ArrayList is flexible in terms of number of elements. We can add elements to them.
ArrayList is not strongly typed: we can add elements of different types to it:
> ArrayList myList = new(); myList.Add(1); myList.Add("Example"); myList.Add(true);"

The ArrayList performance is worse then Array performance, because of boxing.

## Generic Collections

Generic collections are objects that take good things from both Array and ArrayList.
- Good thing about Array is that it is strongly typed.
- Good thing about ArrayList is that it is flexible (not fixed size)

Generic Collections are mostly used in the C#.

#### List

List is a generic collection. It is strongly typed and flexible. 

## Interfaces

There are some interfaces that should be pointed out:
- IList
- IEnumerable
- IAsyncEnumerable