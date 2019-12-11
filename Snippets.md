```
dw "output application/json --- 1 to 100000000000 map {id: \$ }" 
```

```
dw "output application/json --- 1 to 100000000000 map {id: \$ }" | dw "input payload application/json --- payload map (item) -> isEven(item.id)" 
```
-----------
- Stream capable

fun reduce<T>(@StreamCapable values:Array<T>, callback: (T,T) -> T): T =
    values match {
        case [x ~ xs] -> doReduce(xs, callback, values)
        case [] -> dw::Runtime::fail("Reduce on empty array")
    }

fun doReduce<T>(values:Array<T>, callback: (T,T) -> T, acc: T): T =
    values match {
        case [x ~ xs] -> doReduce(xs, callback, callback(x, acc))
        case [] -> acc
    }

- Tail Recursive

%dw 2.0
fun fibo(n: Number) = 
    if(n <= 1) 
        1
    else
        fibo(n - 1) + fibo(n - 2)    
---
dw::util::Timer::duration(() -> fibo(25))


%dw 2.0

@TailRec()
fun fibo(n: Number, a: Number = 0, b: Number = 1) = 
    if(n == 0) 
        a
    else if(n == 1) 
        b    
    else
        fibo(n - 1, b, a + b)
---
dw::util::Timer::duration(() -> fibo(25))