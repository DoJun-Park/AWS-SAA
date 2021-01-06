## AWS RDS (Relational Database Service) 

RDS는 managed service

+ Postgres
+ MySQL
+ MariaDB
+ Oracle
+ Microsoft SQL Server

<br>

## RDS Backups

RDS에서 백업은 자동적으로 가능

트랜잭션 로그가 5분마다 백업된다.

<br>

## RDS Read Replicas for read scalability

Replication : 백업과 성능향상을 위해 데이터 베이스를 여러대의 서버에 복제하는 행위

최대 5개까지 read replica가능 

Replication is **ASYNC**

<br>

## RDS Multi AZ (Disaster Recovery)

**SYNC** replication - failover to standby

Not used for scaling

&#8251; Read Replicas는 Diaster Recovery(DR)을 위해 multi AZ로 설정되어야 한다.

<br>

## RDS Security - Encryption

만약 master가 암호화되어 있지 않다면, read replica도 암호화되어 있지 않다.

Transparent Data Encryption(TDE) : 응용프로그램의 수정 없이 DB 내부에서 암호화 진행

+ oracle과 sql server에서 가능

In-flight encryption - client에서 나의 db로 데이터가 보내질 때 encryption

+ SSL certificates to encrypt data

&#8251; un-encrypted RDS database를 encrypt하는 방법

1. un-encrypted db의 스냅샷 생성 
2. 스냅샷을 복제하여 encrypt
3. encrypted 스냅샷에서 db복구
4. 새로 복구한 db에 애플리케이션 migrate, 이저 db 제거

<br>

## RDS - IAM Authentication 

MySQL, PostgreSQL에서 동작

비밀번호는 필요없고 authentication token만 필요 (토큰 15분간 유효)



&#8251;  No SSH access, only allow SSL connection

<br>

## Amazon Aurora

MySQL 및 PostgreSQL과 호환되는 완전 관리형 관계형 데이터베이스 엔진

RDS보다 20%비싸지만 더 효율적이다.



One Aurora instance takes writes(master)

master의 Automated failover는 30초 이내이다

나머지는 read

Cross Region Replication을 지원한다.

-> default로 하나의 master, 다중의 read replicas 그리고 그들의 storage는 replicated+self healing+auto expanding



<br>

Aurora DB Cluster

+ Writer Endpoint
+ Reader Endpoint
  + 자동적으로 모든 Read Replica들과 연결한다
  + load balancing과 연결을 도와준다, (로드 밸런싱은 connection level에서 동작)

<br>

## Aurora Security

(= RDS Security)

KMS를 이용해 암호화

SSL을 통한 데이터 이동 중 암호화

IAM token을 통한 인증 가능

can't SSH

<br>

## Aurora Serverless

자동화된 database 인스턴스화 그리고 실제 사용에 기반한 auto-scaling

&#8251; &#8251; **infrequent, intermittent, unpredictable workloads**에 적합 (이와 같은 키워드 나오면 Aurora Serverless 생각)

<br>

## Global Aurora

Aurora Global Database

+ 1 primary Region (Read/Write)
+ 최대 5개의 secondary region
+ 하나의 secondary region에 16개 read replicas

<br>







 





















