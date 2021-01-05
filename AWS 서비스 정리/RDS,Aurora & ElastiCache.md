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

































