# Static Analysis 

* Materialization / Streaming [Wiki](https://en.wikipedia.org/wiki/Random_access)
* Common sube expression elimination [Wiki](https://en.wikipedia.org/wiki/Common_subexpression_elimination)
* Tail Recursive [Wiki](https://en.wikipedia.org/wiki/Tail_call)
* Frame inlinening

# Materialization / Streaming

Iterator vs Array (Random access vs Sequencial)

# Materialization Rule

A Variable needs to be materialized if 
   * it is referenced more than once 
   * being referenced inside a lambda (different scope)

# Streaming

It is never materialize in its entire flow

# Streaming: Verify 

`@StreamCapable`. Fails if it doesn't satisfy our rules

# Common Sube Expression Elmimination

Referencial Transparency

```
{
   a: payload.a.b ,
   b: payload.a.b.c,
   d: payload.a.b.d
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

# Tail Recursion

Last Thing Before Return Call To Your Self

# Tail Recursion

```
fun times(a: String, times: Number, acc: String = "") = 
    if(time == 0)
        acc
    else
        times(a, times, acc ++ a)
```            

# Tail Recursion

```
fun times(a: String, times: Number, acc: String = "") = 
    while(true) {
        if(time == 0)
            return acc
        else
            acc = acc ++ a
            times = times
            a = a
    }            
```        

# Tail Recursion: Verify

`@TailRec`. Fails if it doesn't satisfy our rules