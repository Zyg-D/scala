```scala
// implicits - kad veiktu Seq() ??
import spark.implicits._
import org.apache.spark.sql.functions._
import org.apache.spark.sql.expressions.Window

val df1 = Seq(1491771599L,1491771600L,1491771601L).toDF("unix_timestamp")
val df1 = Seq("q", "w").toDF("col_name")
val df1 = Seq((1, true, 1), (1, true, 0)).toDF("A", "B", "C")
// String with quotemarks
val df = Seq("{'k1':'v1','k2':'v2'}").toDF("c1")
// Array:
val df1 = Seq(
    (Seq("v1", "v2"))
).toDF("arr_col")

val col1 = ($"A" === 1) && ($"B" === true)
```

`[x for x in list if x!=somevalue]` >>> `for (x <- list if x != somevalue) yield x`  
`*[lit(x) for x in list_of_str]` >>> `list_of_str map lit: _*`  
`*list_of_str` >>> probably `list_of_str: _*`  
