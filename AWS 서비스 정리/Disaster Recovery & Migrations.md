## RPO and RTO

+ RPO : Recovery Point Objective (목표 복구 시점)
  + 데이터 손실을 어느 정도까지 허용할 수 있는가?
  + 엄무 중단 시점부터 데이터 손실을 수용할 수 있는 시점
+ RTO : Recovery Time Objective (목표 복수 시간)
  + 얼마나 빨리 백업할 수 있는가?
  + 업무 중단 시점부터 복구되어 가동될 때까지의 시간 목표

<br>

## Disaster Recovery - Pilot Light

only for **critical core** assistance

Primary Site의 db는 주기적으로 AWS로 복제되며 Web Server, App Server의 경우 해당 서버들로부터 복제된 AMI를 미리 대기시켜둠

장애 발생시 Web AMI / App AMI로부터 빠르게 인스턴스를 생성하며 복제된 db로부터 데이터 제공받음 

<br>

## Warm Standby

이름처럼 AWS 내에서 이미 실행된 상태에서 대기하는 것

실제 워크로드를 감당할 정도의 용량을 갖고 있지 않음

장애 발생 후 failover시 scale up을 통해 성능을 워크로드 감당할 수준으로 향상

이미 가동중인 상태이기 때문에 RTO는 낮지만, 성능을 올리는데 시간이 소요됨

<br>

## Multi Site / Hot Site Approach

매우 낮은 RTO - 대신 매우 비쌈

전체 프로덕션 스케일을 AWS와 온프레미스에서 동작

<br>

## DMS - Database Migration Service

데이터를 AWS Cloud로 마이그레이션하거나 온프레미스 인스턴스 간에  또는 클라우드와 온프레미스 간에 마이그레이션

마이그레이션동안 source database를 사용할 수 있는 상태로 유지

복제하는 작업을 수행하기 위해서 반드시 EC2 인스턴스를 생성해야 한다.

<br>

## AWS Schema Conversion Tool (SCT)

기존 데이터베이스 스키마를 한 데이터베이스 엔진에서 다른 데이터베이스 엔진으로 변환할 수 있다.

만약 같은 db엔진으로 마이그레이션을 한다면 SCT를 사용할 필요 없다.

<br>

## AWS DataSync

많은 양의 데이터를 온프레미스에서 AWS로 옮기는 서비스

 









