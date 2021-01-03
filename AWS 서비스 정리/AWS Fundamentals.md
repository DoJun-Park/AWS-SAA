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















