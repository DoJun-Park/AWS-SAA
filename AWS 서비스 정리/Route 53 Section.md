## CNAME vs Alias

+ CNAME : Canonical Name의 약자로 도메인 주소를 또 다른 도메인 주소로 매칭시키는 형태의 DNS 레코드 타입
  + name에 다른 record가 있으면 안됨, 오직 non root domain만 가능
+ Alias : 도메인 주소를 AWS Resource로 매칭시키는 형태
  + name에 다른 record가 있어도 가능. root domain, Non root domain 둘다 가능

<br>

## Simple Routing Policy

hostname을 다른 hostname에 매핑

simple routing policy에는 health check를 할 수 없다.

<br>

## Weighted Routing Policy

요청을 특정 endpoint로 퍼센티지 만큼 제어

두 지역간 트래픽 분산에 용이

<br>

## Latency Routing Policy

낮은 지연 속도를 가지는 리전의 주소 반환

<br>

## Health Check

x번 health check 실패 -> unhealthy (default 3)

x번 health check 성공 -> health (default 3)

default health check interval : 30s

<br>

## Geo Location Routing Policy

Latency 기반과 다름.

**사용자의 위치**에 따라 routing 해주는 policy

<br>

## MultiValue routing Policy

Route 53이 DNS 쿼리에 무작위로 선택된 최대 8개의 정상 레코드로 응답하게 하려는 경우 사용

<br> 









