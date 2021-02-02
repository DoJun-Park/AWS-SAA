## AWS S3

S3 bucket은 자동으로 확장되므로 특정 양의 스토리지 공간을 계획하고 할당할 필요가 없다.

S3는 서버리스 서비스이기 때문에 파일을 저장하는 서버를 직접 관리하거나 패치할 필요가 없으며 컨텐트를 저장하기만 하면 된다.

S3 개체는 S3 개체를 업로드한 AWS 계정에서 소유한다.

S3를 사용하면 정적 웹 사이트를 호스팅할 수 있다. 반면 동적 웹 사이트를 호스팅하기 위해서는 다른 리소스를 사용해야 한다.

S3 bucket은 security group가 없다.

S3는 데이터베이스 테이블에 대한 쿼리를 즉시 지원하는 데이터베이스 기술이 아니기 때문에 이 옵션은 잘못되었다.

<br>

## OAI 

OAI는 CloudFront 통해서만 S3 버킷의 파일을 사용할 수 있도록 하여 보안을 높인다.

<br>

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

Direct Connect를 백업 솔루션으로 사용하면 public internet이기 때문에 작동은 하지만 실패할 위험도 있다. 따라서 **Site to Site VPN**을 백업 연결로 사용한다.

<br>

## AWS Site to Site VPN

AWS Site to Site VPN를 사용하면 사내 네트워크 또는 지사 사이트를 Amazon VPC에 **안전**하게 연결할 수 있다.

<br>

## AWS Global Accelerator

AWS Global Accelerator는 로컬 또는 글로벌 사용자와 함께 애플리케이션의 가용성과 성능을 향상시키는 서비스이다.

애플리케이션 로드 밸런서, 네트워크 로드 밸런서 또는 Amazon EC2 인스턴스와 같은 단일 또는 여러 AWS 영역에서 애플리케이션 엔드포인트에 고정 진입점 역할을 하는 **정적 IP 주소**를 제공한다.

사용량에 따라 비용 지불

<br>

## CloudFront

CloudFront는 CDN(Content Delivery Network) 서비스로, 안전하고 확장 가능한 정적 및 동적 웹 컨텐츠, 비디오 스트림 및 API를 전 세계에 제공한다.

CloudFront는 Edge Locations에서 콘텐츠를 **캐싱**함으로써 S3 버킷에 대한 로드를 줄이고 사용자가 콘텐츠를 요청할 때 빠르게 응답할 수 있도록 지원한다. S3에서 CloudFront까지 데이터 전송 수수료는 발생하지 않는다.

CloudFront도 지리적으로 분산된 사용자에게 정적 컨텐츠를 배포할 수 있다.

CloudFront는 regional edge cache가 있어 모든 유형의 컨텐츠, 특히 시간이 지남에 따라 인기가 떨어지는 경향이 있는 컨텐츠에 유용하다.

<br>

## AWS Global Accelerator vs CloudFront

AWS Global Accelerator와 CloudFront는 AWS 글로벌 네트워크와  전 세계 엣지 위치를 사용하는 별도의 서비스이다. 

CloudFront는 캐시 가능한 컨텐츠(이미지 및 비디오)와 동적 컨텐츠의 성능을 모두 향상시킨다. CloudFront는 <u>HTTP/RTMP</u> 프로토콜 기반 요청을 지원한다.

AWS Global Accelerator는 하나 이상의 AWS Region에서 실행중인 애플리케이션에 가장자리에 있는 패킷을 프록시하여 <u>TCP 또는 UDP</u>를 통해 애플리케이션의 성능을 향상시킨다.

<br>

## CloudWatch

CloudWatch event or CloudWatch alarm로 직간접적으로 lambda function을 트리거하는 것은 자원을 낭비하는 것이다. 

그냥 EC2 Reboot CloudWatch Alarm Action을 통해 인스턴스를 reboot하면 된다. 

CloudWatch 복구 옵션은 시스템 검사 실패에 대해서만 작동하며, 인스턴스 상태 검사 실패에 대해서는 작동하지 않는다.

CloudWatch event를 사용해서 EC2 인스턴스 복구를 직접 트리거할 수는 없다.

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

Application Load Balancer는 요청 수준(7계증)에서 작동하며, 요청 내용에 따라 트래픽을 대상(EC2 인스턴스, 컨테이너, IP 주소 및 람다 기능)에 자동으로 분산시킬 수 있다. 

Application 과 Classic Load Balancer는 IP 주소가 아닌 고정 DNS(=URL)를 노출시킨다.

만약 application이 여러 개별 서비스로 구성된 경우 Application Load Balancer는 ⭐**content-based**(요청 내용에 따라) 요청을 서비스로 라우팅할 수 있다.

+ 호스트 기반 라우팅 : 동일한 로드 밸런서에서 여러 도메인으로 라우팅할 수 있도록 HTTP 헤더의 호스트 필드를 기반으로 클라이언트 요청을 라우팅할 수 있다.
+ 경로 기반 라우팅 : HTTP 헤더의 URL 경로를 기준으로 클라이언트 요청을 라우팅할 수 있다.

ALB는 HTTP 및 HTTPS 트래픽의 로드 밸런싱에 가장 적합하며 microservice 및 container를 포함한 최신 애플리케이션 아키텍처의 제공을 목표로 하는 advanced request routing을 제공한다.

Cross-Zone Load Balancing이 가능하다.

Caching 기능이 없다.

<br>

## Network Load Balancer

Network Load Balancer는 지연 시간이 짧고 초당 수백만 건의 요청으로 확장되는 높은 처리량 워크로드를 포함하는 사례에 적합

Network Load Balancer는 **고정 IP**를 공용 웹에 노출하므로 이러한 IP를 사용하여 애플리케이션에 예측 가능한 방식으로 액세스할 수 있다.

Network Load Balancer는 **IP프로토콜 데이터**를 기반으로 Amazon VPC내의 대상에 대한 연결을 라우팅

Network Load Balancer에서 인스턴스 ID를 사용하여 대상을 지정할 경우 트래픽은 인스턴스의 primary 네트워크 인터페이스에 지정된 primary **private** IP 주소를 사용하여 인스턴스로 라우팅된다. (트래픽을 인스턴스로 라우팅하는데 public IP 주소를 사용할 수 없다.)

Cross-Zone Load Balancing이 불가능하다.

<br>

## Classic Load Balancer

Classic Load Balancer는 여러 Amazon EC2 인스턴스 간에 기본 로드 밸런싱을 제공하며 요청과 연결 level 모두 작동

<br>

## NGINX based load balancer

NGINX는 많은 configuration 작업이 필요하다. 그래서 EC2에 NGINX 로드 밸런서를 구축하면 작동하지만 관리 및 확장 문제가 발생한다.

<br>

## Amazon ElastiCache for Redis

인터넷 규모의 실시간 애플리케이션에 전원을 공급하기 위해 밀리초 미만의 latency를 제공하는 매우 빠른 메모리 내 데이터 저장소이다.

Amazon ElastiCache for Redis는 replication, 고가용성, 클러스터 샤딩을 지원하고 AOF persistence를 이용한 데이터 내구성이 있다. 그리고 백업 및 복구 특징이 있다. Amazon ElastiCache for Redis도 HIPAA 적용 대상 서비스이다. (Memchached는 아님)

+ AOF(Append Only File) : 명령어로 실행될 때마다 기록되는 파일

Amazon ElastiCache for Redis는 캐싱, 채팅/메시지, 게임 리더보드, 지리공간, 기계 학습, 미디어 스트리밍, 큐, 실시간 분석 및 세션 저장소와 같은 <u>실시간 트랜잭션 및 분석 처리</u> 사례에 적합한 솔루션이다.

<br>

## Amazon ElastiCache for Memcached

Amazon ElastiCache for Memcached는 Memcached와 호환가능한 인메모리 key-value 저장소 서비스로 캐시 또는 데이터 저장소로 사용할 수 있다.

Amazon ElastiCache for Memcached는 메모리 내 캐시를 구현하여 액세스 latency를 줄이고, 처리량을 증가시키며, 관계형 또는 NoSQL 데이터베이스의 로드를 줄이는데 매우 적합하다. Amazon ElastiCache for Memcached는 HIPAA에 적합하지 않다.

<br>

## AWS OpsWorks

AWS OpsWorks는 Chef 및 Puppet의 관리 인스턴스를 제공하는 configuration management 서비스이다.

Chef and Puppet은 코드를 사용하여 <u>서버 구성을 자동화</u>할 수 있는 자동화 플랫폼이다.

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

## Transit VPC

Transit VPC를 사용하여 여러 지역의 다양한 VPC와 고객 데이터 센터 간의 연결을 지원할 수 있다.

<br>

## Protection against accidental deletion of objects in Amazon S3

+ Enable versioning on the bucket 
+ Enable MFA delete on the bucket - MFA 삭제를 수행하려면 Amazon S3 버킷에서 개체를 영국적으로 삭제하려면 보조 인증이 필요하다.

<br>

## Redshift Spectrum

Redshift Spectrum는 대규모 데이터set 저장 및 분석을 위해 설계된 <u>페타바이트</u> 규모의 클라우드 기반 데이터 웨어하우스 제품이다.

Redshift Spectrum을 사용하면 데이터를 Amazon Redshift 테이블에 로드할 필요 없이 S3의 파일에서 구조화 및 반구조화된 데이터를 효율적으로 쿼리하고 검색할 수 있다.

<br>

## Amazon Kinesis 

Amazon Kinesis는 **스트리밍 데이터**를 **real-time(실시간)**으로 수집, 버퍼링 및 처리할 수 있는 완전히 관리되고 확장 가능한 서비스이다.

Amazon Kinesis는 모든 규모의 스트리밍 서비스를 비용 효율적으로 처리할 수 있는 주요 기능과 함께 애플리케이션의 요구 사항에 가장 적합한 툴을 선택할 수 있는 유연성을 제공한다.

Kinesis Data Streams는 audio file을 읽을 수 없다.

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

## Auto Scaling group

실행중인 인스턴스에 EC2 Auto Scaling group이 있고, ASG를 삭제하면 그 인스턴스는 종료되고 ASG도 삭제된다.

ASG로 생성된 인스턴스는 기존 인스턴스의 데이터를 자동으로 복사하지 않는다.

Auto Scaling 그룹 내에서 실행중인 인스턴스의 상태가 좋지 않은것으로 확인되면 해당 인스턴스는 종류하고 새 인스턴스를 실행하다.

Auto Scaling은 한 region내의 여러 AZ에 걸쳐 ASG를 포괄하여 지리적 이중화의 안전성과 신뢰성을 활용할 수 있다. 하나의 AZ가비정상적이거나 사용할 수 없게 된다면 Auto Scaling은  영향을 받지 않는 AZ에서 새 인스턴스를 시작한다. 애플리케이션은 매우 중요하며 이를 지원하기 위한 안정적인 아키텍처가 필요하므로, EC2 인스턴스는 중단 없는 서비스를 위해 최소 두 개의 AZ로 유지되어야 한다.

동시에 여러 정책이 ASG에 확장 또는 축소를 지시할 수 있다. 이때 Auto Scaling은 가장 큰 용량을 제공하는 정책을 선택한다.

고가용성(HA)을 위한 최소 용량은 **2**개이다.

<br>

## Auto Scaling group lifecycle hook

Auto Scaling group lifecycle hook을 사용하면 auto scaling 그룹이 인스턴스를 시작하거나 종료할 때 사용자 지정 작업을 수행할 수 있다.

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

S3에서는 ACL을 사용하여 버킷이나 개체에 대해 읽기 또는 쓰기 액세스 권한을 사용자 그룹에 부여할 수 있다. ACL을 사용하면 Amazon S3 리소스에 대한 다른 <u>AWS 계정(특정 user는 안됨) 액세스 권한</u>만 부여할 수 있다. (계정에 대해서 액세스 권한을 주는 것은 가능하나 특정 user에 주는 것은 불가능)

<br>

## Identity and Access Management (IAM)

AWS IAM은 직원이 많은 조직에서 단일 AWS 계정으로 여러 사용자를 생성하고 관리할 수 있도록 지원한다. 

IAM policy는 사용자에게 연결되어 AWS 계정 아래의 사용자가 버킷 또는 개체에 액세스할 수 있는 권한을 중앙 집중식으로 제어할 수 있다. IAM 정책을 사용하면 <u>자신의 AWS 계정 내</u>의 사용자에게만 Amazon S3 리소스에 액세스 할 수 있는 권한을 부여할 수 있다.

+ full admininstratorAccess

  full admininstratorAccess를 가진 IAM 사용자는 루트 계정 사용자에게만 지정된 몇 가지 작업을 제외한 거의 모든 AWS 작업을 수행할 수 있다. 루트 계정 사용자만 수행할 수 있는 AWS 태스크 중 일부는 아래와 같다.

  + change account name or root password or root email address, change AWS support plan, close AWS account, enable MFA on S3 bucket delete, create Cloudfront key pair, register for GovCloud

Authentication -> IAM

<br>

## Cluster placement group

Cluster placement group은 단일 가용성 영역 내의 인스턴스의 논리적 그룹이다. 

Cluster placement groups는 네트워크 지연 시간이 짧거나 네트워크 처리량이 높은 이점을 제공하는 애플리케이션에 권장된다.

<br>

## Spot Instance

Spot Instance는 가장 저렴한 인스턴스로 장애에 대해 복원력이 뛰어난 워크로드에 유용하다.

Spot Instance는 중요한 작업(critical job) 또는 database에 적합하지 않다.

Spot Instance는 볼륨의 예측 불가능한 특성 및 **비용 절감**을 바란다면 on-demand 대신 권장된다.

<br>

## FIFO queue

FIFO queue는 일괄 처리(batching)를 통해 최대 초당 3000개의 메시지를 지원하고, 일괄 처리 없이는 초당 300개의 메시지를 지원한다.

FIFO queue의 이름은 .fifo 접미사로 끝나야 한다.

<br>

## NAT 

NAT는 Public Subnet에 있어 private subnet의 인스턴스가 인터넷에 연결되도록 한다.

### NAT Instance vs NAT gateway

NAT Instance는 Security group와 연결할 수 있다.  Vs NAT gateway는 Security group와 연결할 수 없다.

NAT Instance는 port forwarding을 지원한다. Vs NAT gateway는 port forwarding을 지원하지 않는다.

NAT Instance는 bastian server처럼 사용될 수 있다. Vs NAT gateway는 bastian server처럼 사용될 수 없다. 

NAT Instance는 관리되는 서비스가 아닌 고객이 관리하고 유지해야 한다. Vs NAT gateway는 완전 관리되는 서비스이다.

<br>

## AWS WAF - Web Application Firewall

AWS WAF는 웹 요청을 모니터링하고 악의적인 요청으로부터 웹 애플리케이션을 보호할 수 있는 웹 애플리케이션 방화벽 서비스이다.

AWS WAF는 Application Load balancer, API Gateway, CloudFront에 배치되어 사용될 수 있다.

Application Load balancer와 함께 사용될 경우 ACL의 규칙에 따라 요청을 허용하거나 차단할 수 있고, **지리적(geo) 일치 조건**을 사용하면 뷰어의 **지리적 위치에 따라 애플리케이션 액세스를 제한**할 수 있다.

<br>

## Snowball Edge

Snowball Edge에 저장된 데이터는 S3 버킷에 복사되고 나중에 라이프사이클 정책을 통해 AWS Glacier로 전환될 수 있다.

Snowball Edge의 데이터를 AWS Glacier로 직접 복사할 수는 없다.

<br>

## AWS CloudTrail

AWS CloudTrail은 AWS 계정의 거버넌스, 규정 준수, 운영 감사 및 리스크 감사를 지원하는 서비스이다.

AWS CloudTrail을 사용하면 AWS 인프라 전반의 작업과 관련된 계정 활동을 기록, 지속적으로 모니터링 및 유지할 수 있다. 예를 들어 "누가 이 리소스를 수정하기 위해 API 호출을 했습니까?"와 같은 질문에 응답할 수 있다.

<br>

## Amazon Aurora

Amazon Aurora는 MySQL과 Postgre과 호환되는 완전 관리형  **관계형 데이터베이스** 엔진이다. 

<br>

## Amazon Aurora Global Database

Amazon Aurora Global Database는 전 세계적으로 분산된 애플리케이션을 위해 설계되었으며, 단일 Amazon Aurora 데이터베이스가 여러 AWS 영역에 걸쳐 있을 수 있게 된다. 데이터베이스 성능에 영향을 주지 않고 데이터를 복제하고, 각 지역에서 대기 시간이 짧고 빠른 읽기를 가능하게 하며, 지역 전체의 운영 중단으로부터 재해 복구를 제공한다.

<br>

## AMI

AMI는 자신이 생성된 **지역**에 바운딩되어 있다. 때문에 다른 지역에서 AMI를 사용하기 위해서는 **지역별로 AMI를 복사**해야 한다.

<br>

## Golden AMI

Golden AMI는 configuration(구성), 일관된 보안 패치 및 hardening(강화)를 통해 표준화하는 AMI이다. 또한 로그, 보안, 성능 모니터링 등에 대해 승인한 에이전트도 포함되어 있다. 

<br>

## Lambda

AWS Lambda를 사용하면 서버를 프로비저닝하거나 관리하지 않고도 코드를 실행할 수 있다. 사용하는 컴퓨팅 시간에만 비용을 지불하면 되기 때문에 코드가 실행되지 않을 때는 비용이 들지 않는다.

AWS Lambda를 DynamoDB와 결합하여 IoT 소스에서 키 값 데이터를 처리하고 캡쳐할 수 있다.

Lambda function은 항상 AWS 소유 VPC에서 작동한다.

Lambda는 직접 RESTful API 요청을 다룰 수 없다. API Gateway를 사용하여 사용자 지정 RESTful API를 정의하여 HTTPS를 통해 람다 함수를 호출할 수 있다.

Lambda는 다른 계정에도 write할 수 있다.

Lambda funciton은 실행당 최대 15분까지 실행되도록 구성할 수 있다. 시간초과(timeout)를 1초에서 15분 사이의 값으로 설정할 수 있다.

만약 runtime에 문제가 있을 경우 lambda function의 실행이 실패한다.

<br>

## VPN CloudHub

AWS 사이트 간 VPN 연결이 여러 개인 경우 VPN CloudHub를 사용하여 사이트 간에 보안 통신을 제공할 수 있다.

가상 private gateway에 direct connect 연결을 사용하는 사이트도 AWS VPN CloudHub에 속할 수 있다.

만약 회사 본사는 VPC에 대해 Direct Connect 연결을 가지고 있고, 지점은 VPC에 대한 Site-to-Site 연결을 가지고 있다면 VPN Cloud Hub를 사용하여 지사끼리 뿐아니라 본사와도 데이터를 주고 받을 수 있다.

<br>

## AWS Storage Gateway

AWS Storage Gateway는 on-premise 데이터와 S3에 있는 클라우드 데이터를 서로 액세스할 수 있게하는 하이브리드 클라우드 스토리지 서비스이다. 클라이언트가 사내 데이터 스토리지를 유지하고 애플리케이션을 AWS 클라우드로 이동하기를 원하는 경우 스토리지 게이트웨이를 사용하면 된다.

+ File Gateway

  File Gateway는 애플리케이션 데이터 파일과 백업 이미지를 S3 클라우드 스토리지에 내구성이 뛰어난 개체로 저장하기 위해 클라우드에 원활하게 연결할 수 있는 방법을 제공한다.

  **로컬 캐싱**을 통해 S3의 데이터에 대한 SMB 또는 NFS 기반 액세스를 제공한다.

  File access / NFS => File Gateway

+ Volume Gateway

  클라우드 기반 iSCSI 블록 스토리지 볼륨을 사내 애플리케이션에 제공하도록 Storage Gateway 서비스를 Volume Gateway로 구성할 수 있다.

  로컬 캐시 또는 전체 volume을 사내에 제공하는 동시에 volume의 전체 복사본을 AWS cloud에 저장한다.

  Volumes / Block Storage / iSCSI => Volume Gateway

+ Tape Gateway 

  Tape Gateway를 사용하면 기존 백업 워크플로우를 변경하지 않고도 사내에서 물리적 테이프를 사용하여 AWS의 가상 테이프로 교체할 수 있다.

  VTL Tape solution / Backup with iSCSI => Tape Gateway

<br>

## DynamoDB

DynamoDB는 완벽하게 관리되는 NoSQL 데이터베이스 서비스로서 원활한 확장성과 함께 빠르고 예측 가능한 성능을 제공한다.

default로 모든 DynamoDB 테이블은 CloudTrail 로그에 기록되지 않는 <u>AWS **소유** 고객 마스터 키(CMK)</u>로 암호화된다.

<br>

## DynamoDB Stream

DynamoDB Stream은 DynamoDB 테이블의 항목 변경에 대한 정보의 순서 흐름이다. 테이블에 발생하는 모든 변경 내용의 스트림이 포함된다.

<br>

## DynamoDB - DAX

DAX는 DynamoDB를 위한 완전히 관리되고 가용성이 높은 내장 메모리 **캐시**로서 초당 수백만 번의 요청에서도 밀리초에서 마이크로초까지 최대 10배의 성능 향항을 제공한다.

DAX는 DynamoDB **읽기**를 기본적으로 캐시하는데 사용된다. (쓰기에는 도움이 되지 않는다.)

<br>

## X-Ray

AWS X-Ray는 개발자가 마이크로서비스 아키텍처를 사용하여 구축된 애플리케이션과 같은 분산 애플리케이션을 분석하고 디버깅할 수 있도록 지원한다.

X-Ray를 사용하면 성능 문제 및 오류의 근본 원인을 파악하고 문제를 해결하기 위해 애플리케이션과 기본 서비스가 어떻게 작동하는지 파악할 수 있다.

X-Ray를 사용하여 AWS 계정 간에 데이터를 수집할 수 있다.

<br>

## Amazon Route 53 active-active, active-passive failover Configuration

Amazon Route 53 active-active : 모든 리소스를 대부분의 시간 동안 사용 가능하도록 할 때 이 장애 조치 구성을 사용한다.

Amazon Route 53 active-passive : 기본 리소스 또는 리소스 그룹이 대부분의 시간 동안 사용 가능하도록 하고 보조 리소스 또는 리소스 그룹은 기본 리소스가 사용 불가능할 경우를 대비해 대기 중에 있도록 할 때 이 장애 조치 구성을 사용한다.

<br>

## IAM vs Policy

항목(topic) 또는 대기열(queue)에 대한 액세스를 제어하는 두 가지 방법

1. IAM 사용자 또는 그룹에 정책을 추가합니다. 사용자에게 항목 또는 대기열에 대한 권한을 부여하는 가장 간단한 방법은 그룹을 만들고 그룹에 적절한 정책을 추가한 다음 해당 그룹에 사용자를 추가하는 것입니다. 개별 사용자에 대해 설정한 정책을 추적하는 것보다 사용자를 그룹에서 추가 및 제거하는 것이 훨씬 쉽다.
2. 항목 또는 대기열에 정책을 추가합니다. 항목 또는 <u>다른 AWS 계정</u>의 대기열에 권한을 부여하려는 경우 권한을 부여받을 AWS 계정을 주체로 하는 정책을 추가하는 방법밖에는 없습니다.

대부분 첫번째 방법을 사용하지만, **다른 계정의 사용자에게 권한을 부여해야 하는 경우 두 번째 방법을 사용**해야 한다.

<br>

## Amazon GuardDuty

Amazon GuardDuty는 AWS 계정, 워크로드 및 Amazon S3에 저장된 데이터를 보호하기 위해 악의적 활동 또는 무단 동작을 지속적으로 모니터링하고 보호할 수 있는 위협 탑지 기능을 제공한다.

GuardDuty는 AWS CloudTrail 이벤트, Amazon VPC Flow Logs, DNS 로그 등 여러 AWS 데이터 소스에 걸쳐 수백억 개의 이벤트를 분석한다.

만약 서비스를 사용 안함으로 설정하면 서비스 권한을 포기하고 서비스를 재설정하기 전에 기존 소견(findings) 및 구성을 포함하여 나머지 데이터가 모두 삭제된다.

<br>

## Amazon Transcribe

Amazon Transcribe는 오디오를 텍스트로 쉽게 변환할 수 있는 자동 음성인식 서비스이다.

<br>

## Amazon Athena

Amazon Athena는 표준 SQL을 이용해 S3의 데이터를 쉽게 분석할 수 있는 대화형 쿼리 서비스이다.

Amazon Athena는 서버리스로 관리할 인프라가 없으며 사용자가 실행하는 쿼리에 대해서만 비용을 지불한다.

<br>

## AWS Cognito User Pools

Cognito User pool을 활용하여 기본 제공하는 사용자 관리를 하거나 Facebook, Twitter, Google+ 및 Amazon과 같은 외부 ID 제공자와 통합할 수 있다.

Cognito User pool는 권한 부여를 위해 API Gateway와 통합할 수 있다.

<br>

## Cognito Identity pool

Cognito Identity pool은 사용자에게 기타 AWS 서비스에 대한 사용자 액세스 권한을 부여한다.

<br>

## Amazon EC2 instance store

instance store는 인스턴스에 임시 블록 레벨 저장소를 제공한다. instance store는 매우 높은 IOPS를 가지고 있다.

<br>

## Amazon EventBridge

Amazon EventBridge는 자체 애플리케션, **SaaS** 애플리케이션, AWS 서비스의 데이터를 사용하여 애플리케이션을 쉽게 연결할 수 있게 지원하는 서버리스 이벤트 서비스이다.

Amazon EventBridge는 유일하게 타사 **SaaS** 파트너와 직접 통합되는 이벤트 기반 서비스이다.

<br>

## Blue/Green deployment

서로 다른 버전의 애플리케이션을 실행하는 두 개의 동일한 환경 사이에서 트래픽을 이동하여 애플리케이션을 릴리즈하는 기술이다. 이러한 유형의 배포를 통해 현재 실행중인 애플리케이션 버전에 영향을 주지 않고 녹색 환경에서 기능을 테스트할 수 있다. 녹색 버전이 제대로 동작하고 있다면 만족하고 트래픽을 이전 파란색 환경에서 녹색 환경으로 점차 라우팅한다.

이때 Global Accelerator를 사용하면 클라이언트 디바이스 및 인터넷 해결사의 DNS 캐시에 영향을 받지 않고 트래픽을 점진적으로 또는 녹색 환경과 그 반대로 한 번에 이동할 수 있으며, 트래픽 다이얼 및 엔드포인트 가중치 변경도 몇 초 내에 변경된다.

<br>

## AWS Cost Explorer

AWS Cost Explorer는 동일한 인스턴스 제품군 내에서 인스턴스별로 축소될 수 있는 활용율이 낮은 EC2 인스턴스를 식별하고 예약된 인스턴스 및 절감 계획을 고려하여 AWS 청구서에 미칠 수 있는 영향을 파악할 수 있다.

<br>

## AWS Compute Optimizer

AWS Compute Optimizer는 머신러닝을 사용하여 과거 사용율 메트릭을 분석하여 비용 절감과 성능을 향상시키는 최적의 AWS Compute 리소스를 추천한다.

<br>

## Security Group

Security Group rule은 항상 허용되므로 액세스를 거부하는 규칙은 만들 수 없다. 

만약 A에서 들어오는 트래픽만을 허용하도록 B의 Security Group를 구성하는 방법은 A의 secuity group을 인증하는 규칙을 추가한다.

<br>

## SSE-C

SSE-C(고객 제공 키)가 포함된 서버측 암호화를 사용하면 암호화 키를 관리하고 디스크에 쓸 때 Amazon S3가 암호화를 관리하고 개체에 액세스할 때 암호 해독을 관리한다. 

SSE-C를 사용하면 **시작 시 암호화 키를 제공**하지만 AWS에서 암호화를 수행하도록 할 수 있다.

<br>

## Cloud Formation

Cloud Formation은 AWS 리소스를 자동으로 생성해주는 서비스이다.

Cloud Formation를 사용하면 프로그래밍 언어 또는 간단한 텍스트 파일을 사용하여 **모든 지역 및 계정에서 애플리케이션에 필요한 모든 리소스를 자동화되고 안전하게 모델링 및 프로비저닝**할 수 있다.

<br>

## Amazon Workspaces

Amazon Workspaces는 DaaS(Desktop as a Service)이다. 

Amazon Workspaces를 통해 사용자는 언제 어디서나 지원되는 장치에서 액세스할 수 있는 빠르고 응답성이 뛰어난 데스크톱을 사용할 수 있다.

<br>

## AWS SSO(Single Sign-On)

AWS SSO를 사용하면 여러 AWS 계정 및 비즈니스 애플리케이션에 대한 액세스를 중앙에서 쉽게 관리하고 사용자에게 할당된 모든 계정 및 애플리케이션에 대한 단일 로그인 액세스를 한 곳에서 제공할 수 있다,

<br>

## Pilot Light

Pilot Light는 중요한 **핵심 코어**를 중심으로 전체 운영 환경을 신속하게 프로비저닝할 수 있다.

애플리케이션의 작은 버전은 항상 실행되고 있다.

<br>

## Warm Standby

Warm Standby는 전체 작동 환경의 축소된 버전이 실행되는 DR 시나리오를 설명하는데 사용된다.

AWS 내에서 이미 실행된 상태에서 대기한다.

<br>

## SNI (Server Name Indication)

SNI를 통해 AWS는 동일한 ALB로 **두 개 이상의 인증서**를 쉽게 사용할 수 있다.

<br>











