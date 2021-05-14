# Object types
Defining a type in Ulinc is done via the *Object* keyword. A type definition is composed of parts:
- The domain
- The type signature
- The fields list
- The methods list

----------------------

The domain of the type determines where it sits in the type tree. A domain consists of one or more subdomains, concatenated with periods, and must be specified before a type can be used.

```
Domain <subdomain_1>.<subdomain_2>;
```

Domains can be brought into a type using the *import* keyword.

```
import <subdomain_1>.<subdomain_2>;
```

Once imported, all accessible methods and fields will be available for use in the current scope.

A type signature defines the name of the type, as well as all of the parent types inherited by the type. The inheritance list is preceded by the *inherits* keyword:
```
Object <name> inherits <type_1>, <type_2> { }
```

The name of a type can be any valid identifier which is not already a type name in the current domain.

The object scope is composed of two parts, methods and fields. These two parts taken together make up the type's *members*. A member may either be public or private, private members being accessible only within the domain of the object. Public members are accessible to any scope which imports their domain. By default, all members of a type are **private** unless made explicitly public using the *public* keyword.

Any type members can be accessed from within the object via the *this* keyword. The *this* keyword references the current object scope, and can be used for both methods and fields.

Any type member can be made static using the *static* keyword, which defines it as having only one **instance**. A static member is created once during the lifetime of a type, and cannot reference any *instance* member of a type. All static members are accessibly **by** instance members.

## Constructors

A constructor is a special method within the scope of an object which is called when creating an instance of the object. The constructor should initialize (or *construct*) the object for first time use. Constructors, like all members, are private by default, and must be made public using the *public* keyword. Constructors can call each other during initialization using the *this* keyword as a method, such as: `this()`. Constructors *cannot* be static.

By default, a new type will not have a constructor, and thus cannot be initialized. In order to be used, either a constructor must be made for the type, or it must be inherited by an initializeable sub-type.

```
import ulinc.lang;

Domain example;

Object TestType inherits supertype {
	int x; // Private
	public String y; // Public

	testType() { // inaccessible globally
		// initialization
	}

	public testType(int x) { // accessible globally
		// initialization
		this.x = x;
	}
}
```

## Prototypes

Objects can also serve as abstract templates for more complex types, with or without default implementations. In order to facilitate this functionality, method prototypes must be defined within an object scope:

```
public prototypeMethod(int x);
```

A method prototype contains only the method signature, followed by a semicolon. This signifies that the type is a prototype, and *must be inherited* in order to be initialized. Default constructors may also be provided in order to facilitate initialization, but even if a constructor is provided, any type which contains at least one method prototype *cannot* be directly initialized.

## Static types
A static type is a type which contains only static members. Static types are useful as utility providers, such as math libraries or web interface libraries. Static types *cannot* be initialized, as constructors cannot be static.