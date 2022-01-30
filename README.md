```scala
// implicits - kad veiktu Seq()
import spark.implicits._
import org.apache.spark.sql.functions._

val inputDF = Seq(1491771599L,1491771600L,1491771601L).toDF("unix_timestamp")
```
