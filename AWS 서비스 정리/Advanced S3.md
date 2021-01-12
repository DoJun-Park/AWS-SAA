## S3 MFA-Delete

MFA(Multi Factor Authentication) : 사용자가 AWS 웹 사이트 또는 서비스를 엑세스할 때 사용자의 정규 로그인 자격 증명 외에도 AWS가 지원되는 MFA 메커니즘의 고유 인증을 제출하라고 요청함으로써 보안을 더욱 강화

MFA-Delete를 사용하면 S3 buckets 버저닝을 가능하게 할 수 있다.

bucket owner만이 MFA-Delete를 enable/disable할 수 있다.

<br>

## S3 Replication(CRR & SRR)

source와 dest에서 버저닝이 가능해야한다.

CRR - Cross Region Replication

SRR - Same Region Replication

copying은 비동기

S3에 적절한 IAM 권한을 줘야한다.

replication 전에 생성된 객체는 복제된 object에 들어가지 않는다.

origin bucket에서 삭제한 것은 복제된 bucket에 영향을 주지 않는다.

<br>

## S3 Storage Classes

+ Amazon S3 Standard - General Purpose
  + **High durability** of objects across multiple AZ
  + Use case : **big data analytics**, mobile & gaming applications
+ Amazon S3 Standard - Infrequent Access(IA)
  + **less frequently accessed**, but require **rapid access**
  + High durability of objects across multiple AZ
  + **Low cost**
  + Use case : **disaster recovery**
+ Amazon S3 One Zone - Infrequent Access
  + IA와 같지만 **single AZ**에 저장됨
  + Use case : **secondary backup** copies of on-premise data
+ Amazon S3 Intelligent Tiering
  + **Small monthly monitoring** and auto-tiering fee
  + Automatically move objects between two access tiers based on changing access patterns
+ Amazon Glacier
  + 데이터 보관 및 백업을 목적으로 내구성 있게 저렴한 저장 공간을 보안 기능과 함께 제공
  + **Low cost object storage** - archiving/backup
  + data retained for 10 years
  + Glacier안에 있는 item은 Archive라고 부르고, Archive는 Vaults에 저장됨
+ Amazon Glacier Deep Archive
  + 더 오랜 기간동안 저장 가능
  + 가격 싸다

<br>

## AWS Athena

S3 파일들을 직접 분석할 수 있는 서버리스 서비스

SQL 사용하여 쿼리 실행

<br>

## AWS CloudFront

정적 및 동적 웹 콘텐츠를 사용자에게 더 빨리 배포하도록 지원하는 웹 서비스

예를 들어 일반적인 URL을 사용하여 서비스를 접근하려면 인터넷으로 이루어진 상호 연결된 네트워크의 복잡한 모음을 통해 네트어크에서 다른 네트워크로 요청이 라우팅된다.

CloudFront는 AWS 백본 네트워크를 통해 콘텐츠를 가장 효과적으로 서비스할 수 있는 엣지로 각 사용자 요청을 라우팅하여 콘텐츠 배포 속도를 높인다.

햐



















