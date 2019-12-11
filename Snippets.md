```
dw "output application/json --- 1 to 100000000000 map {id: \$ }" 
```

```
dw "output application/json --- 1 to 100000000000 map {id: \$ }" | dw "input payload application/json --- payload map (item) -> isEven(item.id)" 
```
-----------
 Stream capable

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

    