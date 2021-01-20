## Server side encryption at rest

서버가 데이터를 받은 후 암호화

그리고 데이터는 보내지기 전에 해독된다.

데이터는 데이터 키 덕분에 암호화된 상태로 저장된다.

<br>

## Client side encryption

데이터는 클라이언트에 의해서 암호화되고 절대 서버에서 해독되지 않는다.

데이터를 받은 클라이언트에서 해독된다.

<br>

## AWS KMS(Key Management Service)

암호화 작업에 사용되는 키를 쉽게 생성하고 제어할 수 있도록 지원하는 관리형 서비스

AWS service에서 "encryption"은 대부분 KMS이다.

<br>

## KMS - Customer Master Key (CMK) Types

계정 또는 서비스에서 키에 대한 액세스 권한을 공유하는 기능을 비롯하여 키 관리를 완전히 제어하려면 AWS KMS에서 자체 고객 마스터 키를 생성하면 된다.

+ Symmetric : 절대로 암호화되지 않은 상태로 AWS KMS를 벗어나지 않는 단일 256비트 보안 암호화 키를 나타낸다.
+ Asymmetric : 수학적으로 관련된 키 및 프라이빗 키 페어를 나타낸다.

<br>

## AWS Secrets Manager

암호화된 데이터 키를 보호된 보안 암호 데이터와 함께 저장

주로 RDS 통합을 위해 사용됨

<br>

## CloudHSM (Hardware Security Module)

+ KMS => 암호화용 **소프트웨어** 관리
+ CloudHSM => aws클라우드에서 자체 암호화 키를 손쉽게 생성 및 사용할 수 있도록 지원하는 클라우드 기반 **하드웨어** 보안 모듈

symmetric과 asymmetric 암호화 모두 지원

반드시 CloudHSM Client Software를 사용해야 한다.

<br>

 ## AWS Shield

+ AWS Shield Standard
  + 웹 애플리케이션의 고가용성을 지원하기 위해 SYN/UDP Floods, 반사 공격과 같은 일반적이고 빈번하게 발생하는 인프라 공격으로 부터 보호
  + 추가 비용없이 자동으로 활성화
+ AWS Shield Advanced
  + 더 정교하고 더 큰 규모의 공겨에 대해 강화된 보호 제공
  + DDoS 공격에 대해 거의 실시가능로 알림 제공

<br>

## AWS WAF - Web Application Firewall

클라이언트가 정의한 조건에 따라 웹 요청 허용,차단 또는 모니터링하는 규칙을 구성하여 공격으로부터 웹 애플리케이션을 보호하는 웹 패을리케이션 방화벽이다.

**Application Load Balancer**, **API Gateway**, **CloudFront**에 배치

<br>







