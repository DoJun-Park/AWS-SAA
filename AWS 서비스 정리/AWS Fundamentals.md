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





















