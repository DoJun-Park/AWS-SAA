## EBS Volume

Elastic Block Store Vloume은 인스턴스 중지 및 종료 시에도 데이터를 보존해주고, EBS 스냅샷을 통해 손쉽게 백업할 수 있다.

+ network drive이다.

+ 하나의 AZ에 잠겨있다.
+ Provisioned capacity

<br>

## EBS Volume Type

+ GP2 (SSD) : general purpose SSD 
+ IO 1(SSD) : 고성능 SSD
+ ST 1(HDD) : low cost HDD, 자주 접근, 낮은 가격에 빠른 처리량 / big data
+ SC 1(HDD) : lowest cost HDD, 거의 접근하지 않음

<br>

## EBS Snapshots

EBS에서 현재 데이터 상태를 그래로 저장하는 것

스냅샷은 S3에 저장됨.

encrypted volumed의 스냅샷은 encrypted되어져 있다.

<br>

## EBS vs Instance Store

Instance store은 physically attach되어진다.

+ 매우 높은 IOPS (physical이기 때문에)
+ Block Storage
+ data loss에 대한 리스크 존재

EBS는 network drive 

-> 데이터를 잃어도 상관없고 데이터가 일시적이면 Instance Store

<br>

## EBS RAID Options

some RAID options

+ **RAID 0 (increase performance)**
  + 하나의 데이터를 여러 드라이브에 분산 저장하므로 빠른 입출력이 가능하지만, 하나의 EBS가 실패하면 전체 storage 불가능해짐
  + big disk with a lot of IOPS
+ **RAID 1 (increase fault tolerance)**
  + 두 개의 volume에 각각 모든 데이터가 들어가 있으므로 fault tolerance를 높일 수 있다.
  + 원본과 미러링된 디스크 양쪽에서 읽어올 수 있기 때문에 성능 향상 기대
+ RAID 5
+ RAID 6

<br>

## EFS - Elastic File System

여러 AZ의 EC2 인스턴스들이 하나의 EFS를 사용할 수 있다.

AMI를 기반으로 리눅스와 compatible한다.(not window)

<br>

## EBS vs EFS

+ EBS
  + 한번에 하나의 인스턴스에 부착 가능
  + 다른 AZ로 migrate하려면 snapshot 이용
  + default로 ec2인스턴스가 종료되면 root EBS volume도 종료(이는 설정가능함)
+ EFS 
  + 여러 AZ로부터 100개의 인스턴스가 mount 될 수 있다.
  + Linux 인스턴스만
  + EBS보다는 높은 가격
  + EFS-IA(Infrequent access)로 cost saving할 수 있다.















