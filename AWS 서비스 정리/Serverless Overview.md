## What's serverless?

서버리스는 개발자가 더이상 서버를 관리하지 않아도 되는 새로운 패러다임이다.

코드와 함수를 배치

<br>

## Lambda edge

클라우드 프론트에서 제공하는 기능으로 클라우드 프론트 엣지 상에서 람다함수를 실행한다.

<br>

## DynamoDB

완벽하게 관리되는 **NoSQL** 데이터베이스 서비스로 원활한 확장성과 함게 빠르고 예측 가능한 성능 제공

DynamoDB는 **테이블**로 만들어졌고, 각 테이블은 PK를 가지고 있다.

<br>

## DynamoDB - Provisioned Throughput

테이블은 read/write capacity unit을 제공해야 한다.

+ Read Capacity Units (RCU) : read 처리율
+ Write Capacity Units (WCU) : write 처리율

<br>

## DynamoDB - DAX

DAX = DynamoDB Accelerator

DAX는 DynamoDB와 호환되는 캐싱 서비스로 까다로운 애플리케이션에서 빠른 인 메모리 성능을 활용할 수 있다는 것이 장점

만약 이벤트에 read가 급증하면 **DAX cluster**를 생성한다.

<br>

## DynamoDB Streams

DynamoDB Table의 변경사항에 대한 정보들을 stream형태로 처리할 수 있도록 해주는 기능

스트림은 AWS lambda에 의해 읽혀 처리한다. 

<br>

## API Gateway - Securtiy

### IAM Permissions

**Sig v4**활용 



### Lambda Authrorizer (formerly Custom Authorizer)

 lambda를 사용하여 전달중인 헤더의 토큰 확인 -> lambda는 IAM policy를 사용자에게 리턴



### Cognito User Pools

cognito는 사용자의 lifecycle을 관리

cognito는 authentication(인증)만 지원, authorization(권한)은 지원하지 않는다,

<br>

## API Gateway - Security - Summary

+ IAM
  + 사용자/역할이 이미 AWS account에 있을 때
  + authentication(인증) + authorization(권한)
  + Sig v4 활용
+ Custom Authorizer
  + 제 3자 토근
  + authentication(인증) + authorization(권한) (IAM policy 반환하기 때문)
+ Cognito User Pool
  + 자신의 사용자 풀을 관리 (Facebook, google 등)
  + authentication만 실행









