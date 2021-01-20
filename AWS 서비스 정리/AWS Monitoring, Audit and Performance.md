## AWS CloudWatch Metrics

CloudWatch는 AWS 리소스와 AWS에서 실시간으로 진행중인 애플리케이션을 모니터링한다.

Metric(지표)은 모니터링할 변수

⭐ High Resolution : 1 second

<br>

## CloudWatch Dashboards

Dashboards are <u>global</u>

Dashboards can include **graphs from different regions**

<br>

## EC2 Instance Recovery

어떻게 인스턴스를 자동으로 복구할 수 있는가? -> CloudWatch Alarm으로 모니터하여 복구(recovery)

<br>

## AWS CloudTrail

AWS 계정의 거버넌스, 규정, 운영 감사 등을 지원하는 서비스

CloudTrail은 디폴트로 사용가능

⭐ 만약 AWS에서 리소스가 삭제되었다면, CloudTrail부터 확인!!

<br>

## CloudWatch vs CloudTrail vs Config

+ CloudWatch
  + Monitoring & dashboards
  + Events & Alerting
  + Log Aggregation & Analysis
+ CloudTrail
  + Record API calls
+ Config
  + Record configuration changes

<br>

## AWS STS - Security Token Service

aws 리소스에 제한되고 일시적인 접근할 수 있는 보안 자격 증명을 부여

Token은 1시간동안 유효

다른 계정에서 액세스 가능(<-> access key는 다른 계정에서 안됨)

<br>

## Service Control Policies (SCP)

OU 또는 Account level에 적용

Master Account에는 적용되지 않는다.

<br>

## IAM Permission Boundaries

IAM Policy에서 action을 추가해도 IAM Permission Boundary에 관련 role이 없으면 허가되지 않음.

<br>

## AWS Resource Access Manage (RAM)

클라이언트에게 다른 AWS account가 소유하는 AWS resource를 공유

<br>

## AWS Single Sign-On (SSO)

여러 AWS 계정 및 비즈니스 애플리케이션에 대한 액세스를 중앙에서 손쉽게 관리하고 사용할 수 있는 서비스



