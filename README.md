```scala
// implicits - kad veiktu Seq() ??
import spark.implicits._
import org.apache.spark.sql.types._
import org.apache.spark.sql.functions._
import org.apache.spark.sql.expressions.Window


val df1 = Seq(1491771599L,1491771600L,1491771601L).toDF("unix_timestamp")
val df1 = Seq("q", "w").toDF("col_name")
val df1 = Seq((1, true, 1), (1, true, 0)).toDF("A", "B", "C")

// String with quotemarks
val df = Seq("{'k1':'v1','k2':'v2'}").toDF("c1")

// Array
val df1 = Seq(
    (Seq("v1", "v2"))
).toDF("arr_col")

// Map
val df = Seq(
    ("y", Map("a"->2, "b"->3))
).toDF("c1", "c2")

// NULL provided
val df = Seq[(String, Integer)](
    ("Bob", 16),
    ("Alice", null),
    (null, null)
).toDF("name", "age")

// Struct with field names
case class Person(name: String, age: Int)
case class Car(mileage: Double, owner: Person)
val df = Seq(
    Car(81400.8, Person("John", 37)),
    Car(12090.2, Person("Jane", 25))
).toDF()

// Struct w/o field names
val df = Seq(
    ("a", ("b", "c")),
    ("d", ("e", "f"))
).toDF()

val col1 = ($"A" === 1) && ($"B" === true) || ($"C" === true)
```

`[x for x in list if x!=somevalue]` >>> `for (x <- list if x != somevalue) yield x`  
`*[lit(x) for x in list_of_str]` >>> `list_of_str map lit: _*`  
`*list_of_str` >>> `list_of_str: _*`  

`r"\d"` >>> `raw"\d"`  
`r"^\d$"` >>> `raw"^\d$$"`  
`~c.rlike(r"^\d$")` >>> `!(c.rlike(raw"^\d$$"))`  

`df.col_name` >>> `df.col("col_name")`

```scala
// Average of array
aggregate(
    arr,
    struct(lit(0).alias("sum"), lit(0).alias("count")),
    (acc, x) => struct((acc("sum") + x).alias("sum"), (acc("count") + 1).alias("count")),
    s => s("sum") / s("count")
)
```
