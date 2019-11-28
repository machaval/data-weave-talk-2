# Type System# Type System

Structural / Nominal

# Types

- String
- Boolean
- Number
- Array
- Dates
- Object
- Regex
- Namespace

# Type Parameters

```
fun map<T,Q>(a: Array<T>, callback:(T) -> Q) : Array<Q> = ???
---
[1] map ((item: Number): Boolean -> item == 0)
```
## Constrains

```
Array<Number> => Array<T>
```
```
(Number) -> Boolean => (T) -> Q
```

# Build the ecuations

```
T <= Number
Number <= T
Q <= Boolean
```
# Resolve the ecuation by substitution
```
T = Number
```

```
Number <= Number
Q <= Boolean
```

# Explicit vs Infered

```
var a: String = "123"
```

```
var a = "123"
```

# Links

* https://github.com/igstan/itake-2015
* https://www.youtube.com/watch?v=VEaDsKyDxkY
* https://github.com/igstan/itake-2015
* https://crystal-lang.org/2014/12/06/another-language.html
* http://web.cs.ucla.edu/~palsberg/course/cs239/reading/wand87.pdf

# Static Analysis Optimizations

* Materialization / Streaming [Wiki](https://en.wikipedia.org/wiki/Random_access)
* Common sube expression elimination [Wiki](https://en.wikipedia.org/wiki/Common_subexpression_elimination)
* Tail Recursive [Wiki](https://en.wikipedia.org/wiki/Tail_call)
* Frame inlinening

# Materialization / Streaming

Iterator vs Array (Random access vs Sequencial)

# Materialization Rule

```
A Variable needs to be materialized if it is referenced more than once or being referenced inside a lambda (different scope)
```

# Streaming
It is never materialize

# Common Sube Expression Elmimination

Referencial Transparency

```
{
   a: payload.a.b ,
   b: payload.a.b.c,
   d: payload.a.b
}
```

```
do {
    var fakeVar1= payload.a.b
    var fakeVar2= pfakeVar1.c
    ---
    {
       a: fakeVar1,
       b: fakeVar2,
       d: fakeVar2.d
    }
}
```



