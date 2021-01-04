## AWS Availability Zones

AZ는 자연재해로부터의 영향을 최소화하기 위해 만들어진 구별된 데이터 센터. 

각각의 고대역폭, 초저지연 네트워킹으로 연결되어 있다. 



<br>

## IAM Introduction

IAM은 region 선택할 필요 없다. IAM은 global service

<br>

## Security Groups

만약 time out이 발생한다면 security group 이슈 때문이다.

+ 디폴트로 Inbound traffic은 blocked
+ 디폴트로 outbound traffic은 authorised

<br>

## Elastic IPs

인스턴스를 멈추고 다시 시작하면 public IP는 바뀜 -> 고정된 public IP를 가지고 싶다면 Elastic IP

Elastic IP 사용을 되도록이면 피해라.

<br>

## EC2 User Data

EC2 User data Script를 통해 인스턴스를 bootstrap(인스턴스가 시작될 때 적재되는 프로그램)할 수 있다.

스크립트는 처음 시작때만 실행.

EC2 User data Script는 root user와 실행.

<br>

## EC2 on Demand

사용한만큼 지불

비싼 비용

-> 짧은 기간 그리고 방해받지 않는 워크로드에 추천 (애플리케이션이 어떻게 행동할지 예측 할 수 없는)

<br>

## EC2 Reserved Instances

On-demand보다 75% 비용 절감

-> 고정된 상태의 사용일 때 추천

+ Scheduled Reserved instances
  + time window를 예약해서 사용 가능

<br>

## EC2 Spot Instances

On-demand보다 90% 비용 절감

가장 비용 효과적인 인스턴스

-> 실패에 탄력있는 워크로드에 유용



좋은 사용 combo : reserved instances for baseline + on-demand + spot for peaks

<br>

## EC2 Dedicated Hosts

고객에게 전용으로 제공되는 물리적 서버

<br>

## Spot Fleets

= set of Spot Instances + (optional)On-demand instances

spot instances를 할당하려는 전략

+ 낮은 가격

<br>

Burstable Instances (T2/T3)

예상하지 못한 프로세스가 필요할 때, burst 가능

<br>

## AMI (Amazon Machine Image)

인스턴스를 시작하는 데 필요한 정보를 제공

custom하여 사용도 가능

AMI는 특정 AWS 리전에서 적합하다.

<br>

## AMI Storage

AMI는 **S3**에서 존재

<br>

## Placement Groups

EC2 인스턴스 배치 전략

+ Cluster
  + 단일 가용 영역 내에 있는 인스턴스의 논리적 그룹
    + 장점 : 내트워크가 좋음
    + 단점 : 만약 한 인스턴스가 fail하면 모든 인스턴스가 동시에 fail
    + 사용 - 빅데이터를 빨리 처리해야할 때, low latency와 high network throught가 필요할 때
+ Spread
  + 소규모의 인스턴스 그룹을 다른 하드웨어롤 분산 (상호 관련 오류 낮음)
    + 장점 : 인스턴스 그룹 내 장애 확률 낮음.
    + 단점 : 각 az에 7개의 인스턴스로 제한
    + 사용 - 인스턴스 각각의 fail에 고립되어야 할때
+ Partition
  + 인스턴스를 논리적 파티션에 분산
  + 하나의 AZ에 7개 파티션
  + 파티션끼리의 인스턴스는 서로 공유하지 않는다.
    + 사용 - Kafka, hdfs

<br>

## Elastic Network Interfaces (ENI)

VPC에서 가상 네트워크 카드를 나타내는 논리적 네트워킹 구성 요소

<br>

## EC2 Hibernate

EC2 최대 절전 모드로 나중에 필요할 때 다시 가동시킬 수 있는 기능

루트 EBS 볼륨은 **암호화**되어야 한다.

최대 60일 

<br>

















