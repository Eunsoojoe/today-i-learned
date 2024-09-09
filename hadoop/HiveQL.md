# Book.Data를 활용한 HiveQL 실습

[가이드라인]('https://echo-edu.notion.site/DMF-504d02a0227144aab84a2f9abdf8f995')

0. 터미널 실행, ubuntu에서 VsCode 열기
1. Hardoop, yarn 실행(*꼭 접속 확인) <br>
    `sbin/start-dfs.sh` `sbin/start-yarn.sh`
2. hive 연결 <Br>
    `hiveserver2 --hiveconf hive.server2.thrift.port=10000 --hiveconf hive.root.logger=DEBUG,consol` <br>
    `beeline> !connect jdbc:hive2://localhost:10000`
2. hdfs에 폴더 생성 `hdfs dfs -mkdir {폴더명}` 
3. 데이터 로드 (external 방식) <br>
    `hdfs hdfs -put{폴더 경로} input{hdsf 폴더 경로} `
4. 스키마 입력 및 연결

## 테이블 생성 후 데이터 형변환
- 모든 컬럼을 string으로 가져온 후,
- 가상 View 테이블 생성
- View 테이블의 데이터 타입을 변경
    ``` sql
    CREATE EXTERNAL TABLE ratings (
    user_id STRING,
    isbn STRING,
    rating STRING
    )
    ROW FORMAT DELIMITED
    FIELDS TERMINATED BY ';'
    LINES TERMINATED BY '\n'
    STORED AS TEXTFILE
    LOCATION '/user/ubuntu/input/book/BX-Book-Ratings'
    TBLPROPERTIES ('skip.header.line.count'='1');

    CREATE VIEW ratings_view AS
    SELECT user_id, isbn, CAST(rating AS INT) as rating 
    FROM ratings;

    ```

## With절을 활용하여 서브 쿼리 만들기
- 평점 상위 10개의 book을 추출
- 해당 book이 어떤 연도에 속해있는지(=연도마다 상위 Top10의 책들이 몇개 포함되어 있는지)
    ```sql
    WITH temp AS (
        SELECT b.year, b.isbn, AVG(r.rating)
        FROM books_view b
        JOIN ratings_view r ON b.isbn = r.isbn  
        GROUP BY b.isbn, b.year
        HAVING COUNT(b.isbn) > 9 
        ORDER BY AVG(r.rating) DESC 
        LIMIT 10
    )
    SELECT t.year, COUNT(t.year) AS number_of_books
    FROM temp AS t
    GROUP BY t.year
    ORDER BY COUNT(t.year) DESC
    ```