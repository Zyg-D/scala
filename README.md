```scala
// implicits - kad veiktu Seq() ??
import spark.implicits._
import org.apache.spark.sql.functions._

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
