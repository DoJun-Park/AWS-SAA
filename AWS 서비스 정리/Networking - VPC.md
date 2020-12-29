## Understanding CIDR - IPv4

CIDR은 두 가지 요소를 가진다.

+ base IP (xx.xx.xx.xx) - 범위안에 있는 IP를 나타냄
+ Subnet Mask (/26) - IP에 얼마나 많은 비트가 변할 수 있는지

Ex) /30이 subnet mask라면 32-30=2 -> 2^2=4 -> 4개의 IP 허용

192.168.0.0/24 -> 32-24 = 8 -> 2^8 = 256  -> 192.168.0.0 ~ 192.168.0.255 (256 IP)

<br>

## VPC in AWS - IPv4

VPC = Virtual Private Cloud

region 마다 최대 5개 VPC 가질 수 있다.

VPC CIDR는 다른 네트워크과 overlap되면 안된다.

<br>

## Subnets - IPv4 

AWS는 각각의 subnet에 5개의 IP주소를 예약하고 있다.

때문에 만약 subnet을 생성하면 가능한 IP가 5개 빼고 보여짐.

⭐  만약 EC2 인스턴스에서 29개의 IP 주소가 필요하다면 subnet size는 몇이 되어야 할까?

-> /27의 경우 32-27 = 5, 2^5 = 32 이지만 5개를 미리 예약하고 있으므로 27개가 할당되어 29개를 충족못한다. 때문에 subnet size는 /26이 되어야 한다.

<br>

## Internet Gateways

Internet Gateways는 VPC 인스턴스들이 인터넷과 연결하는 것을 도와준다.

하나의 VPC에 하나의 IGW가 할당됨.

Route table도 설정되어야 한다.

<br>

## NAT Instances - Network Address Translation

Private subnet에 있는 인스턴스들을 internet에 연결하게 해준다.

NAT는 public에서 시작되어야 한다.

<br>

## NAT Gateway

NAT instances보다 더 나은 대안

fault-tolerance를 위해 multiple AZ에 multiple NAT Gateway를 반드시 생성.

<br>

## NAT Instances vs NAT Gateway

[NAT 인스턴스와 NAT 게이트웨이의 차이점](https://docs.aws.amazon.com/ko_kr/vpc/latest/userguide/vpc-nat-comparison.html)

두 가지 모두 private subnet에 있는 인스턴스들을 route를 통해 인터넷에 접근하게 도와준다.

<br>

## DNS Resolution in VPC

VPC에는 해당 VPC에서 시작된 인스턴스가 퍼블릭 IP주소에 해당하는 퍼블릭 DNS 호스트 이름을 받는지 여부와 해당 VPC에 대해 Amazon DNS 서버를 통한 DNS 확인이 지원되는지 결정하는 속성이 있다.

+ enableDnsSupport (=DNS Resolution setting)
  + DNS 확인이 지원되는지 나타냄
  + default True
+ enableDnsHostname (=DNS Hostname setting)
  + 퍼블릭 IP 주소를 갖는 인스턴스가 해당하는 퍼블릭 DNS 호스트 이름을 받는지 여부를 나타냄
  + 이 속성이 `true`이고 `enableDnsSupport` 속성도 `true`로 설정되어야 VPC의 인스턴스가 퍼블릭 DNS호스트 이름을 받는다.

**만약 custom DNS domain 이름을 Route S3의 private zone에서 사용한다면, 두 가지 속성 모두 `true`여야 한다.**

<br>

## Network ACLs

NACL은 AWS의 각 VPC 단위로 접근 제어 목록을 만들 수 있고,  VPC로 접근하는 트래픽들에 대한 방화벽을 구성하는 보안계층

기본 설정으로는 모든 인바운드 및 아웃바운드 트래픽을 허용하지만, 사용자 지정 ACL의 경우 새 규칙을 추가하기 전까지 모든 트래픽을 거부한다.

NACL을 여러 서브넷과 연결할 수 있지만, 서브넷은 한 번에 하나의 네트워크 ACL에만 연결할 수 있다.

NACL에는 번호가 매겨진 규칙 목록이 포함되어 있는데, 가장 낮은 번호가 지정된 규칙부터 확인하여 실행한다.

Ex) 규칙 #100 -> ALLOW,  asterisk(*) -> DENY

<br>

## Network ACLs vs Security Groups

**Security Group**은 인스턴스에 대한 인바운드&아웃바운드 트래픽을 제어하는 가상 방화벽의 역할을 한다. 

둘의 차이점

+ ACL은 Request/Response 모두에 관여하며 다른 서브넷 및 외부에서 들어오거나 나가는 요청/응답에 관여.
+ Security Group은 Request에만 관여하며 같은 서브넷, 다른 서브넷 및 외부에서 들어오는 요청의 수신/발신에 관여

<br>

## VPC Peering 

서로 다른 VPC간 통신이 가능하도록 연결하는 것

VPC Peering은 transitive하지 않다. 만약 a와 b가 연결되어 있고 b와 c가 연결되어 있다고 해서 a와 c가 연결되는 것은 아니다.

VPC Peering 연결 이후에 각 VPC간 실제 통신을 하기 위해서는 AWS 콘솔의 VPC의 Route Table에서 별도의 설정이 필요하다.

<br>

## VPC Endpoint

VPC Endpoint는 가상 장치로 VPC와 AWS 서비스를 private connection할 수 있도록 한다. 예를 들어 인스턴스에서 S3에 엑세스 할 때, 인터넷 게이트웨이나 NAT등이 필요 없이 VPC Endpoint로 가능하다.

