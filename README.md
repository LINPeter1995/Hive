# Hive

角色：提供 Hadoop 上的 SQL 查詢能力。

用途：讓使用者能像用 SQL 一樣操作儲存在 HDFS 上的資料。

運作方式：Hive 會把 SQL 轉成 MapReduce 或 Spark 作業去執行。

優點：門檻低、適合熟悉資料庫的使用者。

限制：非即時查詢，執行效能取決於底層執行引擎。

# 常用語法

1. 建立內部表（Managed Table）

CREATE TABLE table_name (
    col1 STRING,
    col2 INT,
    col3 DOUBLE
)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY ','
STORED AS TEXTFILE;

2. 建立外部表（External Table）

CREATE EXTERNAL TABLE table_name (
    col1 STRING,
    col2 INT
)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY ','
LOCATION '/user/hive/external/table_name';

3. 匯入本地檔案（LOCAL）

LOAD DATA LOCAL INPATH '/path/to/file.csv'
INTO TABLE table_name;

4. 匯入 HDFS 檔案

LOAD DATA INPATH '/user/hive/warehouse/file.csv'
OVERWRITE INTO TABLE table_name;

5. 基本查詢

SELECT * FROM table_name;

6. 條件查詢（WHERE）

SELECT col1, col2
FROM table_name
WHERE col2 > 100;

7.  排序（ORDER BY / SORT BY / DISTRIBUTE BY）

SELECT * FROM table_name ORDER BY col1;

8. 分組與聚合（GROUP BY）

SELECT col1, COUNT(*) 
FROM table_name
GROUP BY col1;

9. JOIN 語法

SELECT a.col1, b.col2
FROM table_a a
JOIN table_b b
ON a.id = b.id;

10. LIMIT

SELECT * FROM table_name LIMIT 10;

11. 查看所有表

SHOW TABLES;

12. 查看表結構

DESCRIBE table_name;

13. 刪除表格
    
DROP TABLE table_name;

14. 更名表格
    
ALTER TABLE old_name RENAME TO new_name;

15. 匯出查詢結果
    
INSERT OVERWRITE DIRECTORY '/user/hive/output/'
ROW FORMAT DELIMITED
FIELDS TERMINATED BY ','
SELECT * FROM table_name;

16. 其他常用

SET hive.cli.print.header=true;
SET hive.execution.engine=mr;









