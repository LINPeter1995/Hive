# Hive

角色：提供 Hadoop 上的 SQL 查詢能力。

用途：讓使用者能像用 SQL 一樣操作儲存在 HDFS 上的資料。

運作方式：Hive 會把 SQL 轉成 MapReduce 或 Spark 作業去執行。

優點：門檻低、適合熟悉資料庫的使用者。

限制：非即時查詢，執行效能取決於底層執行引擎。
