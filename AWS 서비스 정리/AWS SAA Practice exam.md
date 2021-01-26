## S3 Performance

+ Multi-Part upload - can help parallelize uploads (크기가 큰 파일을 부분으로 나눠서)

  ​							 - 파일의 크기가 100MB보다 크면 권장하고, 5GB보다 크면 무조건 사용

+ S3 Transfer Acceleration (upload only) - Increase transfer speed by transferring file to an AWS edge location which will forward the data to the S3 bucket in the target region

<br>

## Amazon S3 One Zone-Infrequency Access

Amazon S3 One Zone-IA는 액세스 빈도는 낮지만 필요한 경우 빠른 액세스가 필요한 데이터용이다. 최소 3개의 AZ에 데이터를 저장하는 다른 S3 스토리지 클래스와 달리 S3 One Zone-IA는 단일 AZ에 데이터를 저장해서 S3 Standard-IA보다 20% 저렴하다.

개체를 <u>S3 Standard에서 S3 One Zone-IA로 전환하기까지 최소 저장 기간</u>은 **30일** 이다.

<br>

## Amazon S3 Standard -Infrequency Access

Amazon S3 Standard -IA는 액세스 빈도는 낮지만 필요한 경우 빠른 액세스가 필요한 데이터용이다. 

Amazon S3 Standard -IA는 높은 내구성, 높은 처리량 및 짧은 대기 시간을 제공하며 GB당 스토리지 가격과 GB당 검색 비용을 낮춘다. 이러한 저비용과 고성능의 조합으로 장기 스토리지, 백업 및 재해 복구 파일의 데이터 저장소로 이상적이다. 하지만 가용성 영역 전체에서 중복 스토리지를 사용하기 때문에 S3 One Zone-IA보다 비용이 더 많이 든다.

<br>

## AWS Direct Connect

AWS Direct Connect는 사내에서 AWS로 전용 네트워크 연결을 쉽게 설정할 수 있는 클라우드 서비스 솔루션이다. 

AWS Direct Connect를 사용하면 네트워크와 AWS Direct Connect 위치 중 하나 간에 전용 네트워크 연결을 설정할 수 있다. 

AWS Direct Connect은 프로비저닝하는데 상당한 시간이 소요되고, 특정 사용 사례에 대한 overkill이다.

<br>

## AWS Site to Site VPN

AWS Site to Site VPN를 사용하면 사내 네트워크 또는 지사 사이트를 Amazon VPC에 **안전**하게 연결할 수 있다.

<br>

## AWS Global Accelerator

AWS Global Accelerator는 로컬 또는 글로벌 사용자와 함께 애플리케이션의 가용성과 성능을 향상시키는 서비스이다.

애플리케이션 로드 밸런서, 네트워크 로드 밸런서 또는 Amazon EC2 인스턴스와 같은 단일 또는 여러 AWS 영역에서 애플리케이션 엔드포인트에 고정 진입점 역할을 하는 **정적 IP 주소**를 제공한다.

사용량에 따라 비용 지불

<br>

## CloudWatch

CloudWatch event or CloudWatch alarm로 직간접적으로 lambda functino을 트리거하는 것은 자원을 낭비하는 것이다. 

그냥 EC2 Reboot CloudWatch Alarm Action을 통해 인스턴스를 reboot하면 된다. 

<br>

## Amazon FSx for Lustre

Amazon FSx for Lustre는 고성능 파일 시스템을 쉽고 효과적인 비용으로 생성 및 실행할 수 있다. 이는 병렬 및 분산 방식의 파일 시스템이다.

머신 러닝, 고성능 컴퓨팅(HPC), 비디오 처리와 같은 워크로드에 사용된다.

Amazon FSx for Lustre는 S3와 통합되어 Lustre 파일 시스템으로 데이터 세트를 쉽게 처리할 수 있다.

⭐ High-performance, parallel and distributed => Amazon FSx for Lustre

<br>

## Amazon EMR

Amazon EMR은 Apache Spark, Apache Hive, Apache HBase 등과 같은 오픈 소스 툴을 사용하여 방대한 양의 데이터를 처리할 수 있는 클라우드 빅데이터 플랫폼이다. 

<br>

## Amazon Glue

Amazon Glue는 고객이 분석을 위해 데이터를 쉽게 준비하고 로드할 수 있도록 지원하는 완전히 관리되는 ETL(Extract, Transform, Load) 서비스이다.

<br>

## Application Load Balancer

Application Load Balancer는 들어오는 애플리케이션 트래픽을 EC2 인스턴스, 컨테이너, IP 주소 및 람다 기능과 같은 여러 대상에 자동으로 분산시킬 수 있다. 

만약 application이 여러 개별 서비스로 구성된 경우 Application Load Balancer는 **content-based**(요청 내용에 따라) 요청을 서비스로 라우팅할 수 있다.

+ 호스트 기반 라우팅 : 동일한 로드 밸런서에서 여러 도메인으로 라우팅할 수 있도록 HTTP 헤더의 호스트 필드를 기반으로 클라이언트 요청을 라우팅할 수 있다.
+ 경로 기반 라우팅 : HTTP 헤더의 URL 경로를 기준으로 클라이언트 요청을 라우팅할 수 있다.

ALB는 HTTP 및 HTTPS 트래픽의 로드 밸런싱에 가장 적합하며 microservice 및 container를 포함한 최신 애플리케이션 아키텍처의 제공을 목표로 하는 advanced request routing을 제공한다.

Cross-Zone Load Balancing이 가능하다.

<br>

## Network Load Balancer

Network Load Balancer는 지연 시간이 짧고 초당 수백만 건의 요청으로 확장되는 높은 처리량 워크로드를 포함하는 사례에 적합

Network Load Balancer는 **IP프로토콜 데이터**를 기반으로 Amazon VPC내의 대상에 대한 연결을 라우팅

Network Load Balancer에서 인스턴스 ID를 사용하여 대상을 지정할 경우 트래픽은 인스턴스의 primary 네트워크 인터페이스에 지정된 primary **private** IP 주소를 사용하여 인스턴스로 라우팅된다. (트래픽을 인스턴스로 라우팅하는데 public IP 주소를 사용할 수 없다.)

Cross-Zone Load Balancing이 불가능하다.

<br>

## Classic Load Balancer

Classic Load Balancer는 여러 Amazon EC2 인스턴스 간에 기본 로드 밸런싱을 제공하며 요청과 연결 level 모두 작동

## NGINX based load balancer

NGINX는 많은 configuration 작업이 필요하다. 그래서 EC2에 NGINX 로드 밸런서를 구축하면 작동하지만 관리 및 확장 문제가 발생한다.

<br>

## Amazon ElastiCache for Redis

인터넷 규모의 실시간 애플리케이션에 전원을 공급하기 위해 밀리초 미만의 latency를 제공하는 매우 빠른 메모리 내 데이터 저장소이다.

Amazon ElastiCache for Redis는 replication, 고가용성, 클러스터 샤딩을 지원하고 AOF persistence를 이용한 데이터 내구성이 있다. 그리고 백업 및 복구 특징이 있다. Amazon ElastiCache for Redis도 HIPAA 적용 대상 서비스이다.(Memchached는 아님)

+ AOF(Append Only File) : 명령어로 실행될 때마다 기록되는 파일

Amazon ElastiCache for Redis는 캐싱, 채팅/메시지, 게임 리더보드, 지리공간, 기계 학습, 미디어 스트리밍, 큐, 실시간 분석 및 세션 저장소와 같은 <u>실시간 트랜잭션 및 분석 처리</u> 사례에 적합한 솔루션이다.

<br>

## Amazon ElastiCache for Memcached

Amazon ElastiCache for Memcached는 Memcached와 호환가능한 인메모리 key-value 저장소 서비스로 캐시 또는 데이터 저장소로 사용할 수 있다.

Amazon ElastiCache for Memcached는 메모리 내 캐시를 구현하여 액세스 latency를 줄이고, 처리량을 증가시키며, 관계형 또는 NoSQL 데이터베이스의 로드를 줄이는데 매우 적합하다. Amazon ElastiCache for Memcached는 HIPAA에 적합하지 않다.

<br>

## AWS OpsWorks

AWS OpsWorks는 Chef 및 Puppet의 관리 인스턴스를 제공하는 configuration management 서비스이다.

Chef and Puppet은 코드를 사용하여 서버 구성을 자동화할 수 있는 자동화 플랫폼이다.

OpsWorks를 사용하면 Chef and Puppet를 사용하여 EC2 인스턴스 또는 사내 컴퓨팅 환경에서 서버가 구성, 배포 및 관리되는 방법을 자동화할 수 있다.

<br>

## AWS RDS

Amazon RDS는 multi-AZ 배포를 사용하는 DB 인스턴스에 대한 고가용성 및 failover를 제공한다.

Multi-AZ 배포에서 Amazon RDS는 다른 가용성 영역에 synchronous 대기 복제본을 자동으로 프로비저닝하고 유지한다.

관리자가 개입하지 않고도 데이터베이스 작업을 최대한 빨리 재개할 수 있도록 Amazon RDS에서 failover가 자동으로 처리된다. failover시에 Amazon RDS는 DB 인스턴스에 대한 CNAME을 전환하여 대기 상대를 기다리면 새로운 primary가 된다.

Multi-AZ는 <u>URL은 같고 failover는 자동화되며 CNAME이 standby DB를 가리키도록 자동으로 업데이트됨을 의미</u>한다.

<br>

## transit gateway

transit gateway는 VPC를 상호 연결하거나 VPC를 **사내 네트워크**와 연결하는데 사용할 수 있는 네트워크 전송허브이다.

<br>

## Protection against accidental deletion of objects in Amazon S3

+ Enable versioning on the bucket 
+ Enable MFA delete on the bucket - MFA 삭제를 수행하려면 Amazon S3 버킷에서 개체를 영국적으로 삭제하려면 보조 인증이 필요하다.

<br>

## Redshift Spectrum

Redshift Spectrum는 대규모 데이터set 저장 및 분석을 위해 설계된 <u>페타바이트</u> 규모의 클라우드 기반 데이터 웨어하우스 제품이다.

Redshift Spectrum을 사용하면 데이터를 Amazon Redshift 테이블에 로드할 필요 없이 S3의 파일에서  구조화 및 반부조화된 데이터를 효율적으로 쿼리하고 검색할 수 있다.

<br>

## Amazon Kinesis 

Amazon Kinesis는 **스트리밍 데이터**를 **real-time(실시간)**으로 수집, 버퍼링 및 처리할 수 있는 완전히 관리되고 확장 가능한 서비스이다.

<br>

## Amazon API Gateway

Amazon API Gateway는 너무 많은 요청에 의해 API가 압도되는 것을 방지하기 위해 토큰 버킷 알고리즘을 사용하여 요청을 조절한다.

Amazon API Gateway는 계정의 모든 API에 대한 정상 상태 속도 및 버스트에 대한 제한을 설정한다,

<br>

## VPC Sharing

VPC Sharing을 통해 여러 AWS 계정이 EC2 인스턴스, RDS 인스턴스, Redshift 클러스터 및 람다 함수와 같은 애플리케이션 리소스를 고유 및 중앙 관리되는 VPC로 생성할 수 있다. 이 설정을 위해 VPC를 소유하는 계정은 AWS Organization의 동일한 조직에 속한 다른 계정과 하나 이상의 서브넷을 공유한다. 서브넷이 공유되면 참가자는 공유된 서브넷에서 응용 프로그램 리소스를 보거나 수정 또는 삭제할 수 있다.

주의할 점은 <u>소유자 계정은 VPC 자체를 공유할 수는 없고 **서브넷**을 통해 공유해야 한다.</u>

<br>

## AWS credentials on the EC2

EC2 인스턴스에서 AWS 자격 증명을 유지하는 것은 잘못된 보안 관행이다. 대신 IAM role을 사용하여 EC2 인스턴스에서 실행되는 응용 프로그램의 임시 자격 증명을 관리한다. 이 role은 응용 프로그램이 다른 AWS 리소스를 호출할 때 사용할 수 있는 임시 사용 권한을 제공한다.

<br>

## Auto Scaling group lifecycle hook

Auto Scaling group lifecycle hook를 사용하면 auto scaling 그룹이 인스턴스를 시작하거나 종료할 때 사용자 지정 작업을 수행할 수 있다.

<br>

## lifecycle hook

lifecycle hook을 사용하면 auto scaling 그룹이 인스턴스를 시작하거나 종료할 때 인스턴스를 일시 중지하여 사용자 지정 작업을 수행할 수 있다.

<br>

## EC2 instance meta data

EC2 instance meta data는 실행 중인 인스턴스를 구성하거나 관리하는데 사용할 수 있는 인스턴스에 대한 데이터이다.

<br>

## EC2 instance user data

EC2 instance user data는 인스턴스를 시작할 때 구성 스크립트 형식으로 지정한 데이터이다.

<br>

## Access Control Lists (ACLs)

S3에서는 ACL을 사용하여 버킷이나 개체에 대해 읽기 또는 쓰기 액세스 권한을 사용자 그룹에 부여할 수 있다. ACL을 사용하면 Amazon S3 리소스에 대한 다른 <u>AWS 계정(특정 user는 안됨) 액세스 권한</u>만 부여할 수 있다.

<br>

## Identity and Access Management (IAM)

AWS IAM은 직원이 많은 조직에서 단일 AWS 계정으로 여러 사용자를 생성하고 관리할 수 있도록 지원한다. 

IAM policy는 사용자에게 연겨되어 AWS 계정 아래의 사용자가 버킷 또는 개체에 액세스할 수 있는 권한을 중앙 집중식으로 제어할 수 있다. IAM 정책을 사용하면 <u>자신의 AWS 계정 내</u>의 사용자에게만 Amazon S3 리소스에 액세스 할 수 있는 권한을 부여할 수 있다.

+ full admininstratorAccess

  full admininstratorAccess를 가진 IAM 사용자는 루트 계정 사용자에게만 지정된 몇 가지 작업을 제외한 거의 모든 AWS 작업을 수행할 수 있다. 루트 계정 사용자만 수행할 수 있는 AWS 태스크 중 일부는 아래와 같다.

  + change account name or root password or root email address, change AWS support plan, close AWS account, enable MFA on S3 bucket delete, create Cloudfront key pair, register for GovCloud

<br>

## Cluster placement group

Cluster placement group은 단일 가용성 영역 내의 인스턴스의 논리적 그룹이다. 

Cluster placement groups는 네트워크 지연 시간이 짧거나 네트워크 처리량이 높은 이점을 제공하는 애플리케이션에 권장된다.

<br>

## Spot Instance

Spot Instance는 가장 저렴한 인스턴스로 장애에 대해 복원력이 뛰어난 워크로드에 유용하다.

Spot Instance는 중요한 작업(critical job) 또는 database에 적합하지 않다.

<br>

## FIFO queue

FIFO queue는 일괄 처리(batching)를 통해 최대 초당 3000개의 메시지를 지원하고, 일괄 처리 없이는 초당 300개의 메시지를 지원한다.

FIFO queue의 이름은 .fifo 접미사로 끝나야 한다.

## NAT 

NAT는 Public Subnet에 있어 private subnet의 인스턴스가 인터넷에 연결되도록 한다.

<br>

## AWS WAF - Web Application Firewall

AWS WAF는 웹 요청을 모니터링하고 악의적인 요청으로부터 웹 애플리케이션을 보호할 수 있는 웹 애플리케이션 방화벽 서비스이다.

AWS WAF는 Application Load balancer, API Gateway, CloudFront에 배치되어 사용될 수 있다.

Application Load balancer와 함께 사용될 경우 ACL의 규칙에 따라 요청을 허용하거나 차단할 수 있고, 지리적(geo) 일치 조건을 사용하면 뷰어의 지리적 위치에 따라 애플리케이션 액세스를 제한할 수 있다.

<br>

## Snowball Edge

Snowball Edge에 정장된 데이터는 S3 버킷에 복사되고 나중에 라이프사이클 정책을 통해 AWS Glacier로 전환될 수 있다.

Snowball Edge의 데이터를 AWS Glacier로 직접 복사할 수는 없다.

<br>

## AWS CloudTrail

AWS CloudTrail은 AWS 계정의 거버넌스, 규정 준수, 운영 감사 및 리스크 감사를 지원하는 서비스이다.

AWS CloudTrail을 사용하면 AWS 인프라 전반의 작업과 관련된 계정 활동을 기록, 지속적으로 모니터링 및 유지할 수 있다.

<br>

