## AWS S3

S3 bucket은 자동으로 확장되므로 특정 양의 스토리지 공간을 계획하고 할당할 필요가 없다.

S3는 **서버리스 서비스**이기 때문에 파일을 저장하는 서버를 직접 관리하거나 패치할 필요가 없으며 컨텐트를 저장하기만 하면 된다.

S3 개체는 S3 개체를 업로드한 AWS 계정에서 소유한다.

S3를 사용하면 **정적 웹 사이트를 호스팅**할 수 있다. 반면 동적 웹 사이트를 호스팅하기 위해서는 다른 리소스를 사용해야 한다.

S3 bucket은 security group가 없다.

S3는 데이터베이스 테이블에 대한 **쿼리를 즉시 지원하는 데이터베이스 기술이 아니다.**

인터넷에서 데이터를 전송할 때, **S3 데이터 전송 요금은 없다**. 또한 **S3TA에서는 가속된 전송에 대해서만 요금을 지불**한다.

S3는 아래의 대상에 이벤트를 게시할 수 있다.

+ Amazon SNS
+ Amazon SQS
+ AWS Lambda

웹 브라우저는 웹 페이지와 다른 도메인 이름을 가진 서버에서 시작된 스크립트의 실행을 차단한다. 스크립트 실행을 허용하는 HTTP헤더들 보내기 위해서 Amazon S3를 CORS(Cross-Origin Resource Sharing)로 구성할 수 있다.

<br>

## AWS S3 Life cycle transition

![스크린샷 2021-02-08 오후 10.35.15](/Users/dojun/Library/Application Support/typora-user-images/스크린샷 2021-02-08 오후 10.35.15.png) 

<br>

## S3 Storage 

미사용 데이터와 전송중인 데이터에 **encryption**을 지원하는 S3 스토리지 클래스는 **S3 Glacier**이다.

<br>

## Type of access control in S3

| Type of Access Control | AWS Account Level Control | User Level Control |
| ---------------------- | ------------------------- | ------------------ |
| IAM Policies           | No                        | Yes                |
| ACLs                   | Yes                       | No                 |
| Bucket Policies        | Yes                       | Yes                |

<br>

## S3 Websites

Amazon S3에서 정적 웹 사이트를 호스팅하려면 웹 사이트 호스팅을 위해 Amazon S3 버킷을 구성한 다음 웹 사이트 콘텐츠를 버킷에 업로드한다.

지역에 따라 S3 Website endpoint는 다음 두 가지 형식을 따른다;

+ 웹 사이트 대시(-) -> <bucket-name>.s3-website.<Region>.amazonaws.com
+ dot(.) -> <bucket-name>.s3-website-<Region>.amazonaws.com

<br>

## OAI 

OAI는 **CloudFront** 통해서만 **S3 버킷**의 파일을 사용할 수 있도록 하여 보안을 높인다.

<br>

## S3 Performance

+ Multi-Part upload - can help parallelize uploads (크기가 큰 파일을 부분으로 나눠서)

  ​							 - 파일의 크기가 100MB보다 크면 권장하고, 5GB보다 크면 무조건 사용

+ S3 Transfer Acceleration (upload only) - Increase transfer speed by transferring file to an AWS edge location which will forward the data to the S3 bucket in the target region

<br>

## Amazon S3 Standard

Amazon S3 Standard는 자주 액세스하는 데이터를 위한 높은 내구성, 가용성 및 성능 객체 스토리지를 제공한다. 

최소 스토리지 지속 시간과 검색 비용이 없다. 문제에서 스토리지 지속 시간이 30일 이내인 경우에는 S3 Standard가 좋은 선택지이다.

<br>

## Amazon S3 One Zone-Infrequency Access

Amazon S3 One Zone-IA는 액세스 빈도는 낮지만 필요한 경우 빠른 액세스가 필요한 데이터용이다. 최소 3개의 AZ에 데이터를 저장하는 다른 S3 스토리지 클래스와 달리 S3 One Zone-IA는 단일 AZ에 데이터를 저장해서 S3 Standard-IA보다 20% 저렴하다.

개체를 <u>S3 Standard에서 S3 One Zone-IA로 전환하기까지 최소 저장 기간</u>은 **30일** 이다.

<br>

## Amazon S3 Standard -Infrequency Access

Amazon S3 Standard-IA는 액세스 빈도는 낮지만 필요한 경우 빠른 액세스가 필요한 데이터용이다. 

Amazon S3 Standard -IA는 높은 내구성, 높은 처리량 및 짧은 대기 시간을 제공하며 GB당 스토리지 가격과 GB당 검색 비용을 낮춘다. 이러한 저비용과 고성능의 조합으로 장기 스토리지, 백업 및 재해 복구 파일의 데이터 저장소로 이상적이다. 하지만 가용성 영역 전체에서 중복 스토리지를 사용하기 때문에 S3 One Zone-IA보다 비용이 더 많이 든다.

<br>

## AWS S3 Intelligent-Tiering

AWS S3 Intelligent-Tiering 스토리지 클래스는 성능에 영향을 미치거나 운영 오버헤드 없이 가장 비용 효율적인 액세스 계층으로 데이터를 자동으로 이동하여 비용을 최적화하도록 설계되었다. 이 기능은 개체를 빈번한 액세스에 최적화된 계층과 간헐적인 액세스에 최적화된 저비용 계층의 두 가지 액세스 계층에 저장하는 방식으로 작동한다.

<br>

## AWS Direct Connect

AWS Direct Connect는 사내에서 AWS로 전용 네트워크 연결을 쉽게 설정할 수 있는 클라우드 서비스 솔루션이다. 

AWS Direct Connect를 사용하면 네트워크와 AWS Direct Connect 위치 중 **하나 간에 전용 네트워크 연결**을 설정할 수 있다. 

AWS Direct Connect은 프로비저닝하는데 상당한 시간이 소요되고, 특정 사용 사례에 대한 overkill이다.

Direct Connect는 탁월한 성능과 보안이 보장된다(private connect). **Site to Site VPN**은 백업 연결로 사용한다.(public connect)

<br>

## AWS Direct Connect plus VPN

AWS Direct Connect plus VPN을 사용하면 **하나 이상**의 AWS Direct Connect 전용 네트워크 연결을 Amazon VPC VPN과 결합할 수 있다.

**AWS Direct Connect 자체는 데이터 센터와 AWS 클라우드 간에 암호화된 연결을 제공할 수 없다**. 때문에 **암호화를 필요**로 한다면 **AWS Direct Connect plus VPN**을 사용한다.

<br>

## AWS Site to Site VPN

AWS Site to Site VPN를 사용하면 사내 네트워크 또는 지사 사이트를 Amazon VPC에 **안전**하게 연결할 수 있다.

AWS Site to Site VPN은 low latency와 high throughput connection을 지원할 수 없다.(transit gateway 마찬가지) / Direct connect는 가능

<br>

## AWS Global Accelerator

AWS Global Accelerator는 로컬 또는 글로벌 사용자와 함께 애플리케이션의 가용성과 성능을 향상시키는 서비스이다.

애플리케이션 로드 밸런서, 네트워크 로드 밸런서 또는 Amazon EC2 인스턴스와 같은 단일 또는 여러 AWS 영역에서 애플리케이션 엔드포인트에 고정 진입점 역할을 하는 **정적 IP 주소**를 제공한다.

사용량에 따라 비용 지불

<br>

## CloudFront

CloudFront는 CDN(Content Delivery Network) 서비스로, 안전하고 확장 가능한 정적 및 동적 웹 컨텐츠, 비디오 스트림 및 API를 전 세계에 제공한다.

CloudFront는 Edge Locations에서 콘텐츠를 **캐싱**함으로써 S3 버킷에 대한 **로드를 줄이고** 사용자가 콘텐츠를 요청할 때 빠르게 응답할 수 있도록 지원한다. S3에서 CloudFront까지 데이터 전송 수수료는 발생하지 않는다.

CloudFront도 **지리적으로 분산된 **사용자에게 정적 컨텐츠를 배포할 수 있다.

CloudFront는 **regional edge cache**가 있어 모든 유형의 컨텐츠, 특히 시간이 지남에 따라 인기가 떨어지는 경향이 있는 컨텐츠에 유용하다.

CloudFront는 1GB 미만인 경우 최적의 성능을 보인다.

CloudFront를 ASG 앞에 위치시키면 대폭 절감된 비용으로 컨텐츠를 안정적으로 배포할 수 있도록 지원하는 **Global Caching** 기능이 있다. 그러면 그만큼 ASG는 확장될 필요가 없다.

CloudFront는 캐싱하기 때문에 **매우 동적인 content에는 적절하지 않다.**

<br>

## CloudFront를 통해 제한된 파일에 액세스 제한

+ **Use CloudFront signed URLs**
  + signed URLs에는 콘텐츠에 대한 액세스를 보다 효과적으로 제어할 수 있는 추가 정보(예: 만료 날짜 및 시간)가 포함되어 있다.
+ **Use CloudFront signed cookies
  + CloudFront signed cookies를 사용하면 현재 URL을 변경하지 않으려는 경우 또는 웹 사이트의 구독자 영역에 있는 모든 파일에 대한 액세스를 제공하려는 경우 콘텐츠에 액세스할 수 있는 사용자를 제어할 수 있다.

HTTPS는 개인 콘텐츠에 대한 액세스를 제한할 수 없다.

<br>

## AWS Global Accelerator vs CloudFront

AWS Global Accelerator와 CloudFront는 AWS 글로벌 네트워크와  전 세계 엣지 위치를 사용하는 별도의 서비스이다. 

CloudFront는 캐시 가능한 컨텐츠(이미지 및 비디오)와 동적 컨텐츠의 성능을 모두 향상시킨다. CloudFront는 **<u>HTTP/RTMP</u>** 프로토콜 기반 요청을 지원한다.

AWS Global Accelerator는 하나 이상의 AWS Region에서 실행중인 애플리케이션에 가장자리에 있는 패킷을 프록시하여 <u>TCP 또는 **UDP**</u>를 통해 애플리케이션의 성능을 향상시킨다.

<br>

## CloudWatch

CloudWatch event or CloudWatch alarm로 직간접적으로 lambda function을 트리거하는 것은 자원을 낭비하는 것이다. 

그냥 EC2 Reboot **CloudWatch Alarm Action**을 통해 인스턴스를 reboot하면 된다. 

**CloudWatch 복구 옵션**은 **시스템 검사 실패**에 대해서만 작동하며, 인스턴스 상태 검사 실패에 대해서는 작동하지 않는다.

CloudWatch event를 사용해서 EC2 인스턴스 복구를 직접 트리거할 수는 없다.

<br>

## Amazon FSx for Lustre

Amazon FSx for Lustre는 **고성능 파일 시스템**을 쉽고 효과적인 비용으로 생성 및 실행할 수 있다. 이는 병렬 및 분산 방식의 파일 시스템이다.

머신 러닝, 고성능 컴퓨팅(HPC), 비디오 처리와 같은 워크로드에 사용된다. 

Amazon FSx for Lustre는 S3와 통합되어 Lustre 파일 시스템으로 데이터 세트를 쉽게 처리할 수 있다.

⭐ **High-performance**, **parallel** and **distributed** => **Amazon FSx for Lustre**

<br>

## Amazon EMR

Amazon EMR은 Apache Spark, Apache Hive, Apache HBase 등과 같은 오픈 소스 툴을 사용하여 방대한 양의 데이터를 처리할 수 있는 클라우드 빅데이터 플랫폼이다. 

<br>

## Amazon Glue

Amazon Glue는 고객이 분석을 위해 데이터를 쉽게 준비하고 로드할 수 있도록 지원하는 완전히 관리되는 ETL(Extract, Transform, Load) 서비스이다.

<br>

## Application Load Balancer

Application Load Balancer는 요청 수준(7계증)에서 작동하며, 요청 내용에 따라 트래픽을 대상(EC2 인스턴스, 컨테이너, IP 주소 및 람다 기능)에 자동으로 분산시킬 수 있다. 

Application Application Load Balancer와 Classic Load Balancer는 IP 주소가 아닌 **고정 DNS(=URL)**를 노출시킨다.

만약 application이 여러 개별 서비스로 구성된 경우 Application Load Balancer는 ⭐**content-based**(요청 내용에 따라) 요청을 서비스로 라우팅할 수 있다.

+ 호스트 기반 라우팅 : 동일한 로드 밸런서에서 여러 도메인으로 라우팅할 수 있도록 HTTP 헤더의 호스트 필드를 기반으로 클라이언트 요청을 라우팅할 수 있다.
+ 경로 기반 라우팅 : HTTP 헤더의 URL 경로를 기준으로 클라이언트 요청을 라우팅할 수 있다.

ALB는 **HTTP 및 HTTPS 트래픽의 로드 밸런싱**에 가장 적합하며 microservice 및 container를 포함한 최신 애플리케이션 아키텍처의 제공을 목표로 하는 advanced request routing을 제공한다.

Cross-Zone Load Balancing이 가능하다.

Caching 기능이 없다.

ALB는 EC2 기반 health check를 할 수 없다.

인스턴스 중 하나에 장애가 발생하면 ALB가 장애 발생 인스턴스로 요청 보내는 것을 중지한다.

<br>

## Network Load Balancer(NLB)

Network Load Balancer는 **지연 시간이 짧고** 초당 수백만 건의 요청으로 확장되는 **높은 처리량** 워크로드를 포함하는 사례에 적합

Network Load Balancer는 **고정 IP**를 공용 웹에 노출하므로 이러한 **IP**를 사용하여 애플리케이션에 예측 가능한 방식으로 액세스할 수 있다.

Network Load Balancer는 **IP프로토콜 데이터**를 기반으로 Amazon VPC내의 대상에 대한 연결을 라우팅

Network Load Balancer에서 인스턴스 ID를 사용하여 대상을 지정할 경우 트래픽은 인스턴스의 primary 네트워크 인터페이스에 지정된 primary **private** IP 주소를 사용하여 인스턴스로 라우팅된다. (트래픽을 인스턴스로 라우팅하는데 public IP 주소를 사용할 수 없다.)

Cross-Zone Load Balancing이 불가능하다.

Bastian Host는 포트 22의 TCP 기반 프로토콜인 SSH를 사용하고 있고, NLB는 TCP 트래픽을 지원하므로 같이 사용될 수 있다.

<br>

## Classic Load Balancer

Classic Load Balancer는 여러 Amazon EC2 인스턴스 간에 기본 로드 밸런싱을 제공하며 요청과 연결 level 모두 작동

<br>

## NGINX based load balancer

NGINX는 많은 configuration 작업이 필요하다. 그래서 EC2에 NGINX 로드 밸런서를 구축하면 작동하지만 관리 및 확장 문제가 발생한다.

<br>

## Amazon ElastiCache for Redis

인터넷 규모의 실시간 애플리케이션에 전원을 공급하기 위해 밀리초 미만의 latency를 제공하는 매우 빠른 메모리 내 데이터 저장소이다.

Amazon ElastiCache for Redis는 replication, 고가용성, 클러스터 샤딩을 지원하고 **AOF persistence**를 이용한 데이터 내구성이 있다. 그리고 백업 및 복구 특징이 있다. Amazon ElastiCache for Redis는 **HIPAA 적용 대상 서비스**이다. (Memchached는 아님)

+ AOF(Append Only File) : 명령어로 실행될 때마다 기록되는 파일

Amazon ElastiCache for Redis는 캐싱, 채팅/메시지, 게임 리더보드, 지리공간, 기계 학습, 미디어 스트리밍, 큐, 실시간 분석 및 세션 저장소와 같은 <u>**실시간 트랜잭션 및 분석 처리**</u> 사례에 적합한 솔루션이다.

<br>

## Amazon ElastiCache for Memcached

Amazon ElastiCache for Memcached는 Memcached와 호환가능한 인메모리 key-value 저장소 서비스로 캐시 또는 데이터 저장소로 사용할 수 있다.

Amazon ElastiCache for Memcached는 메모리 내 캐시를 구현하여 액세스 latency를 줄이고, 처리량을 증가시키며, **관계형** 또는 **NoSQL** 데이터베이스의 로드를 줄이는데 매우 적합하다. Amazon ElastiCache for Memcached는 HIPAA에 적합하지 않다.

<br>

## AWS OpsWorks

AWS OpsWorks는 **Chef 및 Puppet**의 관리 인스턴스를 제공하는 configuration management 서비스이다.

Chef and Puppet은 **코드**를 사용하여 **서버 구성을 자동화**할 수 있는 자동화 플랫폼이다.

OpsWorks를 사용하면 Chef and Puppet를 사용하여 EC2 인스턴스 또는 사내 컴퓨팅 환경에서 서버가 구성, 배포 및 관리되는 방법을 자동화할 수 있다.

<br>

## AWS RDS

Amazon RDS는 multi-AZ 배포를 사용하는 DB 인스턴스에 대한 고가용성 및 failover를 제공한다.

Multi-AZ 배포에서 Amazon RDS는 다른 가용성 영역에 synchronous 대기 복제본을 자동으로 프로비저닝하고 유지한다.

관리자가 개입하지 않고도 데이터베이스 작업을 최대한 빨리 재개할 수 있도록 **Amazon RDS에서 failover가 자동으로 처리**된다. failover시에 Amazon RDS는 DB 인스턴스에 대한 **CNAME**을 전환하여 대기 상대를 기다리면 새로운 primary가 된다.

Multi-AZ는 URL은 같고 failover는 자동화되며 CNAME이 standby DB를 가리키도록 자동으로 업데이트됨을 의미한다.

Multi-AZ는 synchronous(동기식) 복제를 따르고 단일 영역 내에서 최소 두 개의 가용성 영역에 걸쳐 있다. 

Read replica는 asynchronous(비동기식) 복제를 따르고 AZ, Cross-AZ, or Cross-Region 내에 일을 수 있다.

| Multi-AZ deployments    | Multi-Region deployments | Read replicas            |
| ----------------------- | ------------------------ | ------------------------ |
| synchronous replication | synchronous replication  | Asynchronous replication |

<br>

## Database Engine level upgrade for an RDS DB 

데이터베이스 엔진 레벨로 업그레이드하려면 다운타임이 필요하다. RDS DB 인스턴스가 Multi-AZ 배포를 사용하는 경우에는 주(primary) DB 인스턴스와 대기(standby) DB 인스턴스가 동시에 업그레이드된다.

<br>

## Transit gateway

transit gateway는 **VPC를 상호 연결**하거나 **VPC를 온프레미스 네트워크**와 연결하는데 사용할 수 있는 네트워크 전송허브이다.

<br>

## Transit VPC

Transit VPC를 사용하여 여러 지역의 다양한 VPC와 고객 데이터 센터 간의 연결을 지원할 수 있다.

<br>

## Protection against accidental deletion of objects in Amazon S3

+ Enable versioning on the bucket 
+ **Enable MFA** delete on the bucket - MFA 삭제를 수행하려면 Amazon S3 버킷에서 개체를 영국적으로 삭제하려면 보조 인증이 필요하다.

<br>

## Redshift Spectrum

Redshift Spectrum는 대규모 데이터 set 저장 및 분석을 위해 설계된 **페타바이트** 규모의 클라우드 기반 데이터 웨어하우스 제품이다.

Redshift Spectrum을 사용하면 데이터를 Amazon Redshift 테이블에 로드할 필요 없이 **S3의 파일**에서 구조화 및 반구조화된 데이터를 효율적으로 쿼리하고 검색할 수 있다.

웨어하우스는 분석하도록 설계되었고, 데이터베이스는 기록하도록 설계되었다.

<br>

## Amazon Kinesis 

Amazon Kinesis는 **스트리밍 데이터**를 **real-time(실시간)**으로 수집, 버퍼링 및 처리할 수 있는 완전히 관리되고 확장 가능한 서비스이다.

Amazon Kinesis는 모든 규모의 스트리밍 서비스를 비용 효율적으로 처리할 수 있는 주요 기능과 함께 애플리케이션의 요구 사항에 가장 적합한 툴을 선택할 수 있는 유연성을 제공한다.

Kinesis Data Streams는 audio file을 읽을 수 없다.

<br>

## Amazon Kinesis Data Streams(KDS)

Amazon Kinesis Data Streams는 대규모 확장 가능하고 내구성이 뛰어난 실시간 데이터 스트리밍 서비스이다.

사용자는 수신되는 데이터 스트림의 예상 볼륨을 처리하기 위해 **적절한 수의 샤드를 수동으로 프로비저닝**해야 한다. 때문에 데이터의 양에 따라 용량을 자동으로 프로비저닝해야 하는 경우 사용하지 않는다.

Kinesis Data Stream은 애플리케이션에 대한 데이터를 여러 shard로 제공하지만, 실제로 생산자 수보다 훨씬 적은 수의 소비자만 사용할 수 있다. 때문에 만약 생산자 수와 소비자 수가 동일해야 한다면 적절하지 않은 선택지이다.

<br>

## Amazon Kinesis Data Firehose

Kinesis Firehose는 데이터 처리량에 대응하여 **자동으로 확장**되며 지속적인 관리가 필요 없는 완전관리형 서비스이다. 데이터를 로드하기 전에 데이터를 배치, 압축, 변환 및 암호화할 수 있으므로 대상에서 사용되는 스토리지 양을 최소화하고 보안을 강화할 수 있다.

Kinesis Firehose는 S3, Redshift, Elasticsearch or Splunk에만 작성할 수 있다.

<br>

## Amazon API Gateway

Amazon API Gateway는 너무 많은 요청에 의해 API가 압도되는 것을 방지하기 위해 토큰 버킷 알고리즘을 사용하여 요청을 조절한다.

Amazon API Gateway는 계정의 모든 API에 대한 정상 상태 속도 및 버스트에 대한 제한을 설정한다,

API Gateway는 상태 비저장(stateless) 클라이언트-서버 통신을 활성화하고, WebSocket API는 상태 저장(stateful) 클라이언트-서버 통신을 활성화한다.

API Gateway에서 API 캐싱을 활성화하여 엔드포인트의 응답을 캐시할 수 있다.

<br>

## VPC Sharing

VPC Sharing을 통해 여러 AWS 계정이 EC2 인스턴스, RDS 인스턴스, Redshift 클러스터 및 람다 함수와 같은 애플리케이션 리소스를 고유 및 중앙 관리되는 VPC로 생성할 수 있다. 이 설정을 위해 VPC를 소유하는 계정은 AWS Organization의 동일한 조직에 속한 다른 계정과 하나 이상의 **서브넷**을 공유한다. 서브넷이 공유되면 참가자는 공유된 서브넷에서 응용 프로그램 리소스를 보거나 수정 또는 삭제할 수 있다.

주의할 점은 <u>소유자 계정은 VPC 자체를 공유할 수는 없고 **서브넷**을 통해 공유해야 한다.</u>

<br>

## AWS credentials on the EC2

EC2 인스턴스에서 **AWS credentials**을 유지하는 것은 잘못된 보안 관행이다. 대신 **IAM role**을 사용하여 EC2 인스턴스에서 실행되는 응용 프로그램의 임시 자격 증명을 관리한다. 이 role은 응용 프로그램이 다른 AWS 리소스를 호출할 때 사용할 수 있는 임시 사용 권한을 제공한다.

<br>

## Auto Scaling group

실행중인 인스턴스에 EC2 Auto Scaling group이 있고, ASG를 삭제하면 그 인스턴스는 종료되고 ASG도 삭제된다.

ASG로 생성된 인스턴스는 기존 인스턴스의 데이터를 자동으로 복사하지 않는다.

Auto Scaling 그룹 내에서 실행중인 인스턴스의 상태가 좋지 않은것으로 확인되면 해당 인스턴스는 종류하고 새 인스턴스를 실행하다.

Auto Scaling은 한 **region내의 여러 AZ**에 걸쳐 ASG를 포괄하여 지리적 이중화의 안전성과 신뢰성을 활용할 수 있다. 하나의 AZ가 비정상적이거나 사용할 수 없게 된다면 Auto Scaling은  영향을 받지 않는 AZ에서 새 인스턴스를 시작한다. 애플리케이션은 매우 중요하며 이를 지원하기 위한 안정적인 아키텍처가 필요하므로, EC2 인스턴스는 중단 없는 서비스를 위해 **최소 두 개의 AZ**로 유지되어야 한다.

동시에 여러 정책이 ASG에 확장 또는 축소를 지시할 수 있다. 이때 Auto Scaling은 **가장 큰 용량을 제공하는 정책을 선택**한다.

고가용성(HA)을 위한 최소 용량은 **2**개이다.

<br>

## Auto Scaling group lifecycle hook

Auto Scaling group lifecycle hook을 사용하면 auto scaling 그룹이 **인스턴스를 시작하거나 종료할 때 사용자 지정 작업을 수행**할 수 있다.

<br>

## lifecycle hook

lifecycle hook을 사용하면 auto scaling 그룹이 인스턴스를 시작하거나 종료할 때 인스턴스를 일시 중지하여 사용자 지정 작업을 수행할 수 있다.

<br>

## Rebalancing Activities

Auto scaling과 달리 **rebalancing activity**는 EC2 auto scaling은 **이전 인스턴스를 종료하기 전에 새 인스턴스를 시작**하므로 재조정으로 인해 애플리케이션의 성능이나 가용성이 저하되지 않는다.

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

Spot Instance는 **가장 저렴한 인스턴스**로 장애에 대해 복원력이 뛰어난 워크로드에 유용하다.

Spot Instance는 중요한 작업(critical job) 또는 database에 적합하지 않다.

가장 저렴한 옵션이지만 중단할 수 없거나 특정 시간 내에 완료해야 하는 작업에는 적합하지 않다.

Spot Instance는 볼륨의 예측 불가능한 특성 및 **비용 절감**을 바란다면 on-demand 대신 권장된다.

Spot request가 지속되면 spot request가 중단된 후 다시 열린다.

Spot block(지속 시간)을 가진 spot instance는 중단되지 않도록 설계되었다.

Active spot request를 취소해도 연결된 인스턴스는 종료되지 않는다.

<br>

## Spot Fleets

Spot Fleet은 사용자의 요구에 맞는 Spot Instance 풀을 선택하고 해당 Fleet의 목표 용량을 충족하기 위해 Spot Instance를 시작합니다.

Spot Fleets = set of Spot Instances + (optional) On-Demand Instances

가장 저렴한 spot instance를 선택해서 최저 가격 전략으로 최적할 수 있다.

<br>

## FIFO queue

FIFO queue는 일괄 처리(batching)를 통해 최대 초당 3000개의 메시지를 지원하고, **일괄 처리 없이**는 **초당 300개**의 메시지를 지원한다.

작업당 일괄 처리할 메세지와 지원하는 메세지의 비는 1:300이다. 만약 FIFO 대기열에서 초당 최대 1200개의 메시지를 지원할 수 있도록 하려면 작업당 4개의 메시지를 처리해야 한다.

FIFO queue의 이름은 .fifo 접미사로 끝나야 한다.

<br>

## NAT 

NAT는 Public Subnet에 있어 private subnet의 인스턴스가 인터넷에 연결되도록 한다.

NAT를 설치하고 나서는 인터는 트래픽이 NAT를 가리키도록 프라이빗 서브넷의 라우팅 테이블을 업데이트 해야 한다.

<br>

## NAT Instance vs NAT gateway

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

## AWS Snowmobile

AWS Snowmobile은 매우 많은 양의 데이터를 AWS로 이동하는 데 사용되는 엑사바이트 규모의 데이터 전송 서비스이다. 세미 트레일러 트럭을 통해 최대 100PB까지 전송할 수 있다.

10PB 이상의 대규모 데이터셋을 이동할 때 권장하고, **10PB미만** 또는 **여러 위치에 분산**되어 있는 데이터셋의 경우 **Snowball**을 사용한다.

<br>

## AWS Snowball

AWS Snowball 서비스는 물리적 스토리지 장치를 사용하여 Amazon S3와 고객의 온사이트 데이터 스토리지 위치 간에 대량의 데이터를 인터넷 속도보다 빠른 속도로 전송한다.

Snowball Edge Storage Optimized 장치는 **80TB**의 데이터를 처리할 수 있다.

<br>

## Snowball Edge

Snowball Edge는 대역폭이 제한되거나 원격, 연결 끊김 또는 더 엄격 환경에서 데이터를 전송하는 고객에게 오프라인 데이터 전송에 적합하다.

Snowball Edge에 저장된 데이터는 S3 버킷에 복사되고 나중에 라이프사이클 정책을 통해 AWS Glacier로 전환될 수 있다. Snowball Edge의 데이터를 AWS Glacier로 직접 복사할 수는 없다.

<br>

## Snowball vs Snowball Edge

AWS Snowball은 이제 서비스 전체를 가리키며 Snowball Edge는 이 서비스가 사용하는 최신 디바이스 유형을 가리킵니다. 때로는 Snowball Edge를 AWS Snowball 디바이스로 통칭하기도 합니다. 초기 Snowball 하드웨어 디자인은 데이터 전송용으로만 사용되었습니다. Snowball Edge에는 네트워크 연결을 사용할 수 없는 경우에도 로컬로 컴퓨팅을 수행할 수 있는 추가 기능이 탑재되어 있습니다.

<br>

## AWS CloudTrail

AWS CloudTrail은 AWS 계정의 거버넌스, 규정 준수, 운영 감사 및 리스크 감사를 지원하는 서비스이다.

AWS CloudTrail을 사용하면 AWS 인프라 전반의 작업과 관련된 계정 활동을 기록, 지속적으로 모니터링 및 유지할 수 있다. 예를 들어 "누가 이 리소스를 수정하기 위해 API 호출을 했습니까?"와 같은 질문에 응답할 수 있다.

<br>

## AWS Config

AWS Config는 AWS 리소스의 구성을 평가 및 감사할 수 있는 서비스이다. 

AWS Config를 사용하면 AWS 리소스 간의 구성 및 관계 변경 사항을 검토하고, 세부 리소스 구성 기록을 자세히 살펴보고, 내부 지침에 지정된 구성에 대한 전반적인 준수 여부를 확인할 수 있다.

AWS Config를 통해 "x 시점에서 AWS 리소스가 어떻게 보이는지"와 같은 질문에 답할 수 있다.

<br>

## Amazon Aurora

Amazon Aurora는 MySQL과 Postgre과 호환되는 완전 관리형  **관계형 데이터베이스** 엔진이다. 

<br>

## Amazon Aurora serverless

Amazon Aurora serverless는 Amazon Aurora의 온디맨드 auto scaling 구성이다. 애플리케이션 요구 사항을 기반으로 자동으로 시작 및 종료하고 용량을 확장 또는 축소한다. **완전 관리형 auto scaling** 솔루션으로 <u>간헐적 또는 예측 불가능한 워크로드</u>를 위한 간단하고 비용 효율적인 옵션이다.

OLTP 애플리케이션의 디비 설계는 관계 모델에 적합하므로 OLTP 시스템을 관계형 데이터베이스로 유추할 수 있다. Aurora serverless는 OLTP 데이터베이스로 0개의 서버로 축소하고 여러 개의 서버로 확장할 수 있는 데이터베이스를 만드는 완벽한 방법이다.

<br>

## Amazon Aurora Global Database

Amazon Aurora Global Database는 전 세계적으로 분산된 애플리케이션을 위해 설계되었으며, 단일 Amazon Aurora 데이터베이스가 여러 AWS 영역에 걸쳐 있을 수 있게 된다. 데이터베이스 성능에 영향을 주지 않고 데이터를 복제하고, 각 지역에서 대기 시간이 짧고 빠른 읽기를 가능하게 하며, 지역 전체의 운영 중단으로부터 재해 복구를 제공한다.

<br>

## AMI

AMI는 자신이 생성된 **지역**에 바운딩되어 있다. 때문에 다른 지역에서 AMI를 사용하기 위해서는 **지역별로 AMI를 복사**해야 한다.

AMI는 snapshot을 기반으로 하기 때문에 다른 영역에서 자동으로 snapshot을 생성한다. 

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

Lambda funciton은 실행당 최대 **15분**까지 실행되도록 구성할 수 있다. **시간초과(timeout)**를 1초에서 15분 사이의 값으로 설정할 수 있다.

만약 **runtime에 문제**가 있을 경우 **lambda function의 실행이 실패**한다.

lambda는 지역별로 계정당 1000개의 동시 실행을 지원한다. 만약 이러한 동시성(consistency) 할당량을 초과해서 제한을 높으려면 AWS 지원팀에 문의해야 한다.

<br>

## VPN CloudHub

다수의 Site-to-Site VPN 연결을 사용하는 경우 VPN CloudHub를 사용하여 사이트 간에 보안 통신을 제공할 수 있다.

가상 private gateway에 direct connect 연결을 사용하는 사이트도 AWS VPN CloudHub에 속할 수 있다.

만약 회사 본사는 VPC에 대해 Direct Connect 연결을 가지고 있고, 지점은 VPC에 대한 Site-to-Site 연결을 가지고 있다면 VPN Cloud Hub를 사용하여 지사끼리 뿐아니라 본사와도 데이터를 주고 받을 수 있다.

<br>

## AWS Storage Gateway

AWS Storage Gateway는 on-premise 데이터와 S3에 있는 클라우드 데이터를 서로 액세스할 수 있게하는 하이브리드 클라우드 스토리지 서비스이다. 클라이언트가 사내 데이터 스토리지를 유지하고 애플리케이션을 AWS 클라우드로 이동하기를 원하는 경우 스토리지 게이트웨이를 사용하면 된다.

+ File Gateway

  File Gateway는 애플리케이션 데이터 파일과 백업 이미지를 S3 클라우드 스토리지에 내구성이 뛰어난 개체로 저장하기 위해 클라우드에 원활하게 연결할 수 있는 방법을 제공한다.

  **로컬 캐싱**을 통해 S3의 데이터에 대한 **SMB(Server Message Block)** 또는 **NFS** 기반 액세스를 제공한다.

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

default로 모든 DynamoDB 테이블은 CloudTrail 로그에 기록되지 않는 AWS **소유** 고객 마스터 키**(AWS owned CMK)**로 암호화된다.

<br>

## DynamoDB Stream

DynamoDB Stream은 DynamoDB 테이블의 항목 변경에 대한 **정보의 순서 흐름**이다. 테이블에 발생하는 모든 변경 내용의 스트림이 포함된다.

<br>

## DynamoDB - DAX

DAX는 DynamoDB를 위한 완전히 관리되고 가용성이 높은 내장 메모리 **캐시**로서 초당 수백만 번의 요청에서도 밀리초에서 마이크로초까지 최대 10배의 성능 향항을 제공한다.

DAX는 DynamoDB **읽기**를 기본적으로 **캐시**하는데 사용된다. (쓰기에는 도움이 되지 않는다.)

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

## Amazon Route 53 health check

Route 53이 활성화되면 개별 ELB 노드에 대한 상태 점검을 자동으로 구성하고 관리한다. 또한 ELB가 수행하는 EC2 인스턴스 상태 점검을 활용한다.

Route 53 DNS failover는 EC2 인스턴스와 ELB의 상태 검사 결과를 결합하여 로드 밸런서의 상태와 EC2 인스턴스에서 실행 중인 애플리케이션의 상태를 평가할 수 있다.

<br>

## Amazon Route 53 TTL

TTL DNS recursive resolver가 이 레코드에 관한 정보를 캐싱할 시간(초)이다.

만약 TTL에 더 긴 값을 지정하면 recursive resolver가 Router 53에 최신 정보를 요청하기 전에 기간이 더 긴 캐시 값을 사용하므로 레코드 변경이 적용되는데 걸리는 시간이 길어진다.

<br>

## IAM vs Policy

항목(topic) 또는 대기열(queue)에 대한 액세스를 제어하는 두 가지 방법

1. **IAM 사용자 또는 그룹에 정책을 추가**합니다. 사용자에게 항목 또는 대기열에 대한 권한을 부여하는 가장 간단한 방법은 그룹을 만들고 그룹에 적절한 정책을 추가한 다음 해당 그룹에 사용자를 추가하는 것입니다. 개별 사용자에 대해 설정한 정책을 추적하는 것보다 사용자를 그룹에서 추가 및 제거하는 것이 훨씬 쉽다.
2. **항목 또는 대기열에 정책을 추가**합니다. 항목 또는 <u>다른 AWS 계정</u>의 대기열에 권한을 부여하려는 경우 권한을 부여받을 AWS 계정을 주체로 하는 정책을 추가하는 방법밖에는 없습니다.

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

Amazon Athena는 표준 SQL을 이용해 **S3의 데이터를 쉽게 분석할 수 있는 대화형 쿼리 서비스**이다.

Amazon Athena는 **서버리스**로 관리할 인프라가 없으며 사용자가 실행하는 쿼리에 대해서만 비용을 지불한다.

<br>

## AWS Cognito User Pools

Cognito User pool을 활용하여 기본 제공하는 사용자 관리를 하거나 Facebook, Twitter, Google+ 및 Amazon과 같은 외부 ID 제공자와 통합할 수 있다.

Cognito User pool는 권한 부여를 위해 API Gateway와 통합할 수 있다.

Cognito User pool은 **CloudFront 배포와 직접 통합할 수 없고**, 인증을 받으려면 별로의 Lambda@Edge 기능을 생성해야 한다.

<br>

## Cognito Identity pool

Cognito Identity pool은 사용자에게 기타 AWS 서비스에 대한 사용자 액세스 권한을 부여한다.

<br>

## Amazon EC2 instance store

instance store는 인스턴스에 임시 블록 레벨 저장소를 제공한다. instance store는 매우 높은 IOPS를 가지고 있다.

만약 높은 IOPS와 최적의 비용을 찾는다면 io1 대신 instance store가 좋은 선택지이다.

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

Default rules for **default** security group : 동일한 security group에 할당된 **네트워크 인터페이스(및 관련 인스턴스)의 인바운드 트래픽 허용**, **모든 아웃바운드 트래픽 허용**

Default rules for security group that **you create** : **모든 인바운드 트래픽 허용하지 않고**, **모든 아웃바운드 트래픽 허용**

<br>

## SSE-C

SSE-C(고객 제공 키)가 포함된 서버측 암호화를 사용하면 암호화 키를 관리하고 디스크에 쓸 때 Amazon S3가 암호화를 관리하고 개체에 액세스할 때 암호 해독을 관리한다. 

SSE-C를 사용하면 **시작 시 암호화 키를 제공**하지만 AWS에서 암호화를 수행하도록 할 수 있다.

<br>

## SSE-KMS

SSE-KMS는 안전한 고가용성 하드웨어와 소프트웨어를 결합하여 클라우드용 키 관리 시스템을 제공하는 서비스이다.

SSE-KMS는 **감사 추적(audit trail)**이 가능하다.

<br>

## Client Side Encryption

만약 회사의 고유 알고리즘을 사용해서 암호화한다고 하면 Client Side Encryption이다. 

SSE-C,SSE-KMS 그리고 SSE-S3 모두 S3에서 암호화된다.

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

Warm Standby는 전체 작동 환경의 **축소된 버전**이 실행되는 DR 시나리오를 설명하는데 사용된다.

AWS 내에서 이미 실행된 상태에서 대기한다.

<br>

## SNI (Server Name Indication)

SNI는 동일한 IP address로 여러 웹 사이트가 존재할 수 있도록 허용하는 TLS 프로토콜  확장이다. 

SNI를 통해 AWS는 동일한 ALB로 **두 개 이상의 인증서**를 쉽게 사용할 수 있다.

<br>

## Elastic Load Balancer

+ Connection Draining : Auto Scaling이 사용자의 요청을 처리 중인 EC2 인스턴스를 바로 삭제하지 못하도록 방지하는 기능이다.

ELB는 들어오는 트래픽을 여러 AZ에서 여러 대상에 걸쳐 분산시키고 정상 대상만 트래픽을 수신하도록 보장한다. 다른 지역에 배포된 대상에 대해 수신 트래픽을 배포할 순 없다.

<br>

## CNAME vs Alias

|                        | CNAME                          | Alias                |
| ---------------------- | ------------------------------ | -------------------- |
| DNS namespace 지원     | 지원 안함                      | 지원 함              |
| 쿼리에 관해서 요금부과 | 부과 o                         | 부과 x               |
| point                  | 아무 DNS record 가리킬 수 있음 | AWS 자원만 접근 가능 |

<br>

## AWS DataSync

AWS DataSync는 온프레미스 스토리지 시스템과 AWS 스토리지 서비스 간, 그리고 여러 AWS 스토리지 서비스 간의 데이터 이동을 간소화, 자동화 및 가속화하는 온라인 데이터 전송 서비스이다.  DataSync를 사용하여 **활성 데이터를 AWS로 마이그레이션**하거나, 데이터를 아카이브하여 온프레미스 스토리지 용량을 확보하거나, 비즈니스 연속성을 위해 데이터를 AWS로 복제하거나, 분석 및 처리를 위해 데이터를 클라우드로 전송할 수 있다.

<br>

## AWS Transfer Family

AWS Transfer Family는 Amazon S3로 직접 파일 전송을 완벽하게 관리한다.

<br>

## Automatic recovery

EC2 인스턴스가 문제로 인해 손상될 경우 Cloudwatch를 통해 자동으로 복구될 수 있다.

이때 복구된 인스턴스는 인스턴스 ID, 개인 IP 주소, Elastic IP 주소 및 모든 인스턴스 메타데이터를 포함하여 원래 인스턴스와 동일하다. 손상된 인스턴스가 배치 그룹에 있으면 복구된 인스턴스가 배치 그룹에서 실행된다. 

대신 종료된 인스턴스는 복구할 수 없다.

recovery action은 EBS 볼륨이 구성된 인스턴스에서만 지원된다.(instance store volume은 cloudwatch alarm에 의한 자동 복구 지원 안됨)

<br>

## EC2 hibernate

인스턴스를 Hibernate(최대 절전 모드)로 전환하면 AWS가 운영 체제에 최대 절전 모드를 수행하도록 신호를 보낸다. 최대 절전 모드는 내용을 인스턴스 메모리(RAM)에서 EBS 루트 볼륨으로 저장한다. 그런 다음 AWS는 인스턴스의 Amazon EBS 루트 볼륨과 연결된 Amazon EBS 데이터 볼륨을 유지한다.

때문에 오랜 시간 사용을 안하다가 나중에 사용하기 위해 미리 pre-warm이 필요한 경우 사용한다. 

60일 이내 까지 hibernate 가능

<br>

## Availability Zone

한 계정의 AZ us-west-a2는 다른 계정의 us-west-a2와 동일한 위치가 아닐 수 있다. 때문에 계정 간에 가용성 영역을 조정하려면 가용성 영역의 고유하고 일관된 식별자인 **AZ ID**를 이용해야 한다.

<br> 

## AWS Step Function

AWS Step Function을 사용하면 AWS Lambda 및 AWS Glue와 같은 여러 AWS 서비스를 서버리스 워크플로우로 조정하고 오케스트레이트 할 수 있다.  

Step Function은 주어진 사용 사례에 정의된 워크플로우에 따라 글루 ETL 작업과 람다 기능이 순서대로 성공적으로 실행되도록 할 수 있다.

<br>

## AWS Simple Workflow Service(SWF)

Amazon SWF는 개발자가 병렬 또는 순차적 단계를 가진 백그라운드 작업을 구축, 실행 및 확장할 수 있도록 지원한다.

Amazon SWF에서 태스크는 애플리케이션의 논리적 단계 호출을 나타낸다.

Amazon SWF는 오케스트레이션 로직을 완벽하게 제어할 수 있지만, 애플리케이션 개발의 복잡성을 증가시킨다.

<br>

## target tracking scaling group vs step scaling group

두 정책 모두 **CloudWatch alarm**이 울릴 때만 인스턴스를 프로비저닝하는데 사용된다.

target tracking scaling 사용하는 경우

+ Auto Scaling 그룹의 평균 총 CPU 사용량을 40%로 유지하는 경우
+ Application Load Balancer 대상 그룹의 대상 1개당 요청 수를 Auto Scaling 그룹에 필요한 1000개로 유지하는 경우

갑작스런 spike를 처리할 때는 필요한 인스턴스 수를 정확하게 계산할 수 있는 target tracking 정책이 step정책보다 더 효율적이다.

<br>

## Elastic Fabric Adapter

EFA는 EC2 인스턴스에 연결하여 HPC(High Performance Computing) 및 기계 학습 응용 프로그램을 가속화할 수 있는 네트워크 장치이다.

<br>

## AWS Elastic Beanstalk

AWS Elastic Beanstalk는 애플리케이션을 실행하는 인프라에 대해 자세히 알지 못해도 AWS 클라우드에서 애플리케이션을 신속하게 배포하고 관리할 수 있게 해주는 서비스이다.

애플리케이션 코드를 업로드하기만 하면 해당 애플리케이션을 배포하는데 필요한 리소스를 자동으로 파악한다.

<br>

## AWS CloudFormation

AWS CloudFormation는 사용하려는 AWS 리소스를 JSON이나 YAML형식으로 템플릿 파일로 작성하면 이를 분석하여 AWS 리소스를 자동으로 생성해주는 서비스이다.

<br>

## AWS CloudFormation StackSet

AWS CloudFormation StackSet은 단일 작업으로 여러 계정 및 지역에 걸쳐 스택을 생성, 업데이트 또는 삭제할 수 있도록 지원함으로써 스택의 기능을 확장한다. stackset를 사용하면 단일 AWS CloudFormation 템플릿을 사용하여 여러 지역에 걸쳐 AWS 계정에 스택을 생성할 수 있다.

그냥 stack을 사용해서는 AWS 계정 및 지역에 동일한 템플릿을 배포할 수 없다.

<br>

## basic monitoring and detailed monitoring

Basic monitoring은 launch template을 생성하거나 AWS Management Console을 사용하여 실행 구성을 생성할 때 사용된다.

Detailed monitoring은 AWS CLI 또는 SDK를 사용하여 실행 구성을 생성할 때 기본적으로 실행된다.

<br>

## Amazon VPC console wizard

Amazon VPC console wizard는 아래의 4가지 configuration을 제공한다.

1. VPC with a single public subnet
2. VPC with public and private subnets (NAT)
3. VPC with public and private subnets and AWS Site-to-Site VPN access
4. VPC with a **private** subnet only and AWS Site-to-Site VPN access - 네트워크가 인터넷에 노출되지 않고 Amzaon 인프라를 사용하여 네트워크를 클라우드로 확장하려는 경우 사용

<br>

## Tenancy

launch configuration을 생성할 때, 인스턴스의 배치 tenancy는 null이고 instance tenancy는 VPC의 tenancy 특성에 의해 제어된다. launch configuration tenancy를 기본값으로 설정하고 VPC tenancy를 dedicated(전용)로 설정하면 인스턴스가 dedicated tenancy가 된다. 

만약 launch configuration tenancy 또는 VPC tenancy가 dedicated로 설정되면, instance tenancy 또한 dedicated가 된다.

| Tenancy Value | Description                                                  |
| ------------- | ------------------------------------------------------------ |
| `default`     | Your instance runs on shared hardware.                       |
| `dedicated`   | Your instance runs on single-tenant hardware .               |
| `host`        | Your instance runs on a Dedicated Host, which is an isolated server with configurations that you can control. |

instance를 시작한 후에는 테넌시를 host에서 dedicated로, dedicated에서 host로 변경할 수 있다.



<br>

## SQS short polling vs long polling

SQS는 대기열에서 메시지를 수신할 수 있는  short polling과 long polling을 제공한다. 

기본적으로 대기열은 short polling이다. short polling을 사용하면 쿼리에서 메시지가 발견되지 않더라도 SQS는 응답을 즉시 전송한다.

long polling을 사용하면 SQS가 요청에 지정된 최대 메시지 수까지 사용 가능한 메시지를 하나 이상 수집한 후 응답을 보낸다. 

long polling을 사용하면 빈 수신 수를 줄일 수 있기 때문에 SQS 사용 비용을 줄일 수 있다.

<br>

## SQS message timer

SQS message timer는 대기열에 추가되는 메시지의 초기 미표시 기간을 저정한다.

<br>

## SQS Visability timeout

메시지를 받은 뒤 특정 시간 동안 다른 곳에서 동일한 메시지를 다시 꺼내볼 수 없게 하는 기능이다.

<br>

## S3 Glacier vault

S3 Glacier vault는 archive를 저장하는 저장소이다.

S3 Glacier vault lock은 각 S3 Glacier 볼트마다 볼트 잠금 정책을 사용해 규정 준수 제어 항목을 쉽게 배포하고 적용할 수 있는 기능이다. 볼트 잠금 정책에서는 ‘write once, read many’(WORM) 같은 제어 항목을 지정하여 앞으로 편집하지 못하도록 정책을 잠글 수 있습니다. 일단 잠긴 정책은 더 이상 변경할 수 없다.

<br>

## AWS Managed Microsoft AD vs AD Connector vs Simple AD

AD Connector -> 사내 사용자가 Active Directory 자격 증명으로 AWS 응용 프로그램에 로그인할 수 있다면

AWS Managed Microsoft AD -> 사용자가 5000명 이상이고 AWS 호스팅된 디렉토리와 사내 디렉토리 간에 신뢰 관계를 설정해야 하는 경우

Simple AD -> 사용자가 5000명 이하이고 advanced Microsoft Active Directory와 같이 다른 도메인과 신뢰 관계가 필요하지 않는 경우

<br>

## Service Control Policy(SCP)

SCP는 조직을 관리하는데 사용할 수 있는 정책 중 하나이다. SCP는 조직의 모든 계정에 대해 사용 가능한 최대 권한에 대한 중앙 집중식 제어를 제공하며, 계정이 조직의 액세스 제어 지침 내에서 유지되도록 보장한다.

+ SCP는 root 사용자를 포함하여 연결된 계정의 모든 사용자 및 역할에 영향을 미친다.
+ 사용자 또는 역할에 해당 SCP에 의해 허용되지 않거나 명시적으로 거부된 작업에 대한 액세스 권한을 부여하는 IAM 권한 정책이 있는 경우 사용자 또는 역할은 해당 작업을 수행할 수 없다.
+ SCP는 서비스 관련 역할(service-linked role)에 영향을 주지 않는다.

<br>

## EBS Volume Type

ST1과 SC1 볼륨 유형은 부팅 볼륨으로 사용할 수 없다. / GP2, IO1, instance Store는 부팅 볼륨으로 사용할 수 있다.

<br>

## Elastic File System(EFS) vs Elastic Block Store(EBS)

**EFS**는 **지역별** 스토리지 서비스이다. VS **EBS**는 **개별 AZ**로 범위가 지정된다.

**AMI**는 **지역별** 서비스이다.

<br>

## AWS account root user security recommendations

1. Use a strong password to help protect account-level access to the AWS Management Console.

   강력한 암호를 사용하여 AWS Management Console에 대한 계정 수준 액세스를 보호합니다.

2. Never share your AWS account root user password or access keys with anyone. 

   AWS 계정 루트 사용자 암호 또는 액세스 키를 다른 사람과 공유하지 마십시오.

3. If you do have an access key for your AWS account root user, delete it. If you must keep it, rotate (change) the access key regularly. You should not encrypt the access keys and save them on Amazon S3.

   AWS 계정 루트 사용자에 대한 액세스 키가 있는 경우 삭제합니다. 보관해야 하는 경우 액세스 키를 정기적으로 회전(변경)합니다. 액세스 키를 암호화하여 Amazon S3에 저장해서는 안 됩니다.

4. If you don't already have an access key for your AWS account root user, don't create one unless you absolutely need to.

   AWS 계정 루트 사용자에 대한 액세스 키가 아직 없는 경우 반드시 필요한 경우가 아니면 해당 키를 생성하지 마십시오.

5. Enable AWS multi-factor authentication (MFA) on your AWS account root user account.

   AWS 계정 루트 사용자 계정에서 AWS MFA(다단계 인증)를 사용하도록 설정합니다.

<br>

## Spread placement group

Spread placement group는 서로 분리해야 하는 중요 인스턴스가 적은 응용프로그램이다. 인스턴스는 그룹당 **최대 7**개 까지 존재할 수 있다.

<br>

## Launch Template vs Launch Configuration

**Launch Template**을 사용하면 **On-Demand Instance와 Spot Instance를 모두 사용하여 여러 인스턴스 유형에 걸쳐 용량을 프로비저닝**하여 원하는 확장, 성능 및 비용을 달성할 수 있다.

Launch Configuration은 auto scaling group이 EC2 인스턴스를 시작하는데 사용하는 인스턴스 구성 템플릿이다. **Launch Configuration**을 사용하여  **On-Demand Instance와 Spot Instance를 모두 사용하여 여러 인스턴스 유형에 걸쳐 용량을 프로비저닝할 수는 없다.**

<br>

## IAM Permission boundary

IAM Permission boundary는 IAM entity(user or role)에 대한 권한 경계를 지원한다. (group에는 적용되지 않는다)

IAM Permission boundary는 관리되는 정책을 사용하여 ID 기반 정책이 IAM 엔티티에 부여할 수 있는 최대 사용 권한을 설정하는 고급 기능이다.

<br>

## Secret Manager

Secret Manager는 애플리케이션, 서비스 및 IT 리소스에 액세스하는 데 필요한 기밀을 보호할 수 있다. 또한 전체 라이프사이클에 걸쳐 데이터베이스 자격 증명, API 키 및 기타 암호를 쉽게 순환, 관리 및 검색할 수 있다.

Secrets Manager는 Amazon RDS, Amazon Redsift 및 Amazon DocumentDB에 내장된 통합 기능으로 secret rotation을 제공

<br>

## CloudHSM

CloudHSM은 AWS 클라우드에서 암호화 키를 쉽게 생성하고 사용할 수 있는 클라우드 기반 HSM(하드웨어 보안 모듈)이다.

CloudHSM은 비밀 저장소가 아닌 암호화 서비스이다.

<br>

## EC2 instance in Impaired status

Amazon EC2 auto sacling은 impaired status(손상 상태)의 인스턴스를 즉시 종료하지 않는다. 대신 인스턴스가 복구될 때까지 몇 분 정도 기다린다.

<br>

## Dedicated Instance

Dedicated Instance는 **단일 고객 전용 하드웨어**의 VPC에서 실행되는 Amazon EC2 인스턴스이다.

Dedicated Instance는 사용자 전용 물리적 서버이기도 한다.

Single-tenant hardware => Dedicated Instance

<br>

## Auto Scaling vs Application Load balancer

만약 인스턴스 중 하나에 장애가 발생한다면?

Auto Scaling은 종료한다. VS ALB는 장애 발생 인스턴스로 요청을 보내는 것을 중지한다.

<br>

## Elastic Network Interfaces (ENI)

VPC에서 가상 네트워크 카드를 나타내는 논리적 네트워킹 구성 요소이다.

인스턴스가 생성되면 자동으로 기본 ENI 생성됨

기존 ENI는 인스턴스에서 분리할 수 없지만, 보조 ENI는 분리하여 다른 인스턴스에 연결할 수 있다.

ENI는 EC2 인스턴스에 연결하여 failover로 사용될 수 있다.

<br>

## Batch

Batch job 나오면 **EC2**, Spot instance, Fargate(컨테이너에 적합) 생각하기

<br>

