## AWS CLI on EC2

IAM(Identity and Access Management)는 AWS의 각 객체(사용자, 서비스)에 권한을 주는 서비스이다.

각 권한은 역할이라는 상위 개념으로 모이지게 되고 이렇게 정의된 역할은 각 객체에 할당된다. 이를 **IAM Role**이라 한다.

IAM Role은 EC2 인스턴스에 attach 가능하다. 대신 하나의 EC2 인스턴스에 하나의 IAM Role만 attach 가능																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																																										 <br>

## AWS EC2 Instance Metadata

+ Metadata = EC2 인스턴스에 관한 정보
+ Userdata = EC2 인스턴스의 launch script