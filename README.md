```scala
// implicits - kad veiktu Seq()
import spark.implicits._
import org.apache.spark.sql.functions._

val inputDF = Seq(1491771599L,1491771600L,1491771601L).toDF("unix_timestamp")
val df1 = Seq((1, true, 1), (1, true, 0)).toDF("A", "B", "C")

val col1 = ($"A" === 1) && ($"B" === true)
```
