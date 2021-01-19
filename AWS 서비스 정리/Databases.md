## RDS Overview

+ Managed PostgreSQL/MySQL/Oracle/SQL Server
+ Support for read replica and Multi AZ
+ Use case : Store relational datasets (RDBMS / OLTP)

<br>

## Aurora Overview

+ PostgreSQL/MySQL과 API 호환 가능

+ Auto healing capability(replica 하나 잃으면 자동으로 복구)
+ "Aurora Serverless" 옵션
+ pay per hour

<br>

## ElastiCache Overview

+ Managed Redis / Memcached
+ In-memory data store
+ Not a SQL database
+ Use case : Key/Value store, frequent reads, less writes
+ Sub-millisecond performance, **in memory**

<br>

## DynamoDB Overview

+ AWS proprietary(소유권) technology, managed NoSQL database
+ **Serverless**
+ elasticache처럼 key/value로 대체할 수 있다
+ DynamoDB streams는 AWS Lambda와 통합
+ Use case : Serverless applications development

<br>

## S3 Overview

+ S3 is key/value store
+ big objects에 좋다. (RDSm dynamoDB는 small object)
+ **Serverless**, scales infinitely(max obect size is 5TB)
+ Use case : static files, key value store for big files

<br>

## Athena Overview

+ **Fully Serverless** database 
+ S3에 저장된 데이터 분석하는 SQL 서비스
+ 쿼리마다 pay
+ Use case : serverless queries on S3, log analytics
+ Security : IAM + S3 security

<br>

## Redshift Overview

+ Redshift based on PostgreSQL, but not used for **OLTP**(Online Transaction Processing)
+ **OLAP- online analytical processing** (analytics and **data warehousing**)
+ **Columnar** storage of data (instead of row based)
+ Redshift = Analytics / BI(Business intelligence)/ Data Warehouse

<br>

## Redshift - Snapshots & DR

+ Snapshot - point-in-time backups of a cluster, stored internally in S3

<br>

## Redshift Spectrum

+ 로딩이나 ETL 없이 S3에 있는 엑사바이트 규모의 비정형 데이터에 대해 커리를 실행할 수 있는 Amazon Redshift의 기능
+ S3에 이미 있는 데이터를 로드하지 않고 쿼리한다.
+ 우선적으로 Redshift cluster를 생성해야한다.

<br>

## Neptune

+ fully managed **graph** database
  + High relationship data
+ Neptune  = Graphs

<br>

## ElasticSearch

+ DynamoDB에서는 오직 pk 또는 index로 찾을 수 있지만, ElasticSearch에서는 아무 field로 찾을 수 있다.
+ BIg data application에서 사용된다.
+ ElasticSearch = Search / Indexing



















