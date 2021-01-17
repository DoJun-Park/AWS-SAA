## Amazon SQS - Standard Queue

SQS(Simple Queue Service) : 지속성이 우수하고 사용 가능한 보안 호스팅 대기열을 제공하며 이를 통해 분산 소프트웨어 시스템과 구서 요소를 통합 및 분리할 수 있는 서비스

+ 제한없는 처리량, 큐 안의 메시지 -> auto scaling 또는 용량 늘릴 필요 없다.
+ low latency

중복 메시지를 가지고 있을 수 있다.

메시지의 순서가 순차적이지 않을 수 있다.

<br>

## SQS - Producing Messages

SDK를 통해 SQS에 생성

메시지는 사용자가 삭제할 때까지 유지(디폴트 4일)

<br>

## SQS - Consuming Messages

Consumer는 EC2 instance, server 또는 AWS Lambda등이 될 수 있다

Message를 가져와서 처리, 삭제(DeleteMessage API) 가능

<br>

## SQS - Message Visibility Timeout

consumer에게 메시지가 poll되면 다른 consumer에게는 보여지지 않는다.

"Message visibility timeout"은 디폴트로 30초이다. 그 이후에는 다른 사용자에게 보여진다.

<br>

## Amazon SQS - Dead Letter Queue

사용자가 visibility Timeout 동안 process하는데 fail하면 메시지는 다시 queue로 돌아간다. 이렇게 다시 돌아가는 횟수를 지정하여 횟수가 넘어가면 메세지는 DLQ로 간다.

디버깅에 유용

<br>

## Amazon SQS - FIFO Queue

queue에 FIFO으로 메시지 쌓임

<br>

## Amazon SNS

SNS(Simple Notification Service) : 게시자가 구독자에게 메시지를 전송하는 관리형 서비스

<br>

## AWS Kinesis

데이터 수집구간과 데이터 처리구간 중간에 위치하여 스트리밍 데이터를 처리한다.

Kinesis는 아파치 카프카의 관리된 대안책이다.

실시간 빅데이터에 좋다.

+ 종류
  + Kinesis Streams : 기본적인 스트리밍 큐
  + Kinesis FireHose : Streams + delivery stream(deliver to S3, Redshift and ElasticSearch)
  + Kinesis Analytics : Streams + application(analysis by SQL)

<br>

## Kinesis Streams

Streams는 정렬된 shard/partition으로 나눠진다.

각 shard는 1MB/s incoming이 가능하고, 2MB/s outgoing이 가능하다. 

<u>만약 kinesis stream에서 트래픽이 증가하면 shard를 추가하면 됨.</u>

데이터를 재처리할 수 있다. (<-> SQS는 데이터 한번 소비되면 끝)

Real-time processing

데이터는 1일에서 최대 7일까지 유지하고, 한번 삽입되면 삭제될 수 없다.



<br>

## Kinesis Streams Shards

하나의 스트림은 여러 다른 shard들로 이뤄져있다.

<br>

## AWS Kinesis API - Consumers

consumer는 Kinesis Client Library를 이용하여 효율적으로 사용가능하다.

<br>





