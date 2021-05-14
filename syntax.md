# Syntax
UlinC supports extended syntax for logical operations.

## Anonymous types
An anonymous type can be used for variables or fields which do not need to have a type associated with them. Anonymous types can contain any type of object, or newly constructed types which are not defined in the current domain. When the member access operator is used on an anonymous type, the runtime component searches the type for the requested member, and executes the request if found. Anonymous types can be converted into instance types if a compatible supertype or containing type is available in the current domain.

An anonymous type is declared using the *generic* keyword:
```
generic x;
```

## Loops
The loop keyword defines the start of a loop statement. A loop statement will execute a number of times equal to the requested amount.

The loop keyword is aliased to "for", "foreach", and "while" for convenience, but all perform the same actions. The loop statement can be formatted in several different ways:

```
loop(Type i [:/in] iterable) { }
// Same as foreach

loop(int i = x, y) { }
// Same as for

loop(int i = 0; i < x; ++i) { }
// Same as above

loop(i < x) { }
// Same as while
```

The statement is what determines how the loop behaves, and is unrelated to which keyword you use to declare the loop.

## Templates

Templates allow the programmer to define a delegate type for an object without knowing the type ahead of time. For instance, a list which should contain all one type can be defined as such:

```
Domain example;

Object Type<T> {
	T field;

	T get(int index);

	int indexOf(T object);
}
```