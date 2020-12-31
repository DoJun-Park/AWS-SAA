## RPO and RTO

RTO(Recovery Time Objective) : 목표 복구 시간

RPO(Recovery Point Objective) : 목표 복구 시점

<br>

## Disaster Recovery Strategies

+ Backup and Restore - High RPO
+ Pilot Light - cloud에서 작은 버전의 앱이 항상 돌아갈 때, critical core에 유용
+ Warm Standby - Full system이 동작하지만 크기가 작을때
+ Multi Site - very low RTO, expensive, Full Production Scale이 동작하고 있을 때



<br>

## DMS - Database Migration Service

데이터를 AWS Cloud로 마이그레이션

<br>

## AWS Schema Conversion Tool(SCT)

기존 데이터 베이스 스키마를 한 데이터베이스 엔진에서 다른 데이터베이스 엔진으로 변환

같은 DB엔진끼리 마이그레이팅 할 때는 사용하지 않아도 된다.

<br>

## AWS DataSync

on premise에서 AWS로 많은 양의 데이터를 옮길 때







 