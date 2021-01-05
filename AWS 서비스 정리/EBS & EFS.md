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

+ 높은 IOPS(physical이기 때문에)
+ Block Storage
+ data loss에 대한 리스크 존재

EBS는 network drive 

-> 데이터를 잃어도 상관없고 데이터가 일시적이면 Instance Store

<br>

## EBS RAID Options



















