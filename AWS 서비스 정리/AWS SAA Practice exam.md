## S3 Performance

+ Multi-Part upload - can help parallelize uploads (크기가 큰 파일을 부분으로 나눠서)

  ​							 - 파일의 크기가 100MB보다 크면 권장하고, 5GB보다 크면 무조건 사용

+ S3 Transfer Acceleration (upload only) - Increase transfer speed by transferring file to an AWS edge location which will forward the data to the S3 bucket in the target region

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



