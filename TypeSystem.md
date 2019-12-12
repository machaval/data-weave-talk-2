# Type System

# Kind

Structural / Nominal

# Properties

Soundness / Completeness

# Basic Types

- String
- Boolean
- Number
- Dates
- Regex
- Namespace
- Null
- Object
- Array
- Function
- Any
- Nothing

# Algebraic Data Types

- Union Types: e.g String | Number
- Intersection Types: e.g {name: String} & {age: Number}

# Type Parameters (PlaceHolders)

```
fun map<T, Q>(a: Array<T>, callback:(T) -> Q) : Array<Q> = ???
---
[1] map ((item: Number): Boolean -> item == 0)
```

# Type Parameters 

Top Types

```
fun addAge<T <: {name: String}>(a: T): T & {age:Number} = ???
```

# Type Parameter resolution

```
fun map<T, Q>(a: Array<T>, callback:(T) -> Q) : Array<Q> = ???
---
[1] map ((item: Number): Boolean -> item == 0)
```

# Calculate Constraints

```
Array<T> <= Array<Number>
```
```
(T) -> Q <= (Number) -> Boolean
```

# Build the Equations

```
T <= Number
Number <= T
Q <= Boolean
```
# Resolve the Equation using Substitution

```
T = Number
```

```
Number <= T
Q <= Boolean
```

# Resolve the Equation using Substitution

```
T = Number
```

```
Number <= Number
Q <= Boolean
```

# Resolve the Equation using Substitution

```
T <= Number
```

```
Q <= Boolean
```

# Resolve the Equation using Substitution

```
T = Number
Q <= Boolean
```

# Use Solution On Return Type

```
T = Number
Q <= Boolean
```

```
Array<Q>
```

# Use Solution On Return Type

```
Array<Boolean>
```

# Explicit vs Inferred

```
var a: String = "123"
```

```
var a = "123"
```

# Global Type Inference

Data Flow Graph

# Links

* https://github.com/igstan/itake-2015
* https://www.youtube.com/watch?v=VEaDsKyDxkY
* https://github.com/igstan/itake-2015
* https://crystal-lang.org/2014/12/06/another-language.html
* http://web.cs.ucla.edu/~palsberg/course/cs239/reading/wand87.pdf
