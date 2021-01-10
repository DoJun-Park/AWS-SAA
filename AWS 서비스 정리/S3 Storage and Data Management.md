

⭐ S3 - global service, S3 bucket - localized

<br>

## Amazon S3(Simple Storage Service)

인터넷 스토리지 서비스

+ infinitely scaling

<br>

## Amazon S3 - Buckets

Amazon S3은 object를 bucket에 저장할 수 있도록 한다.

bucket은 globally하게 유일한 이름을 가져야 한다.

<br>

## Amazon S3 - Objects

object는 키를 가지고 있다.

키는 **FULL path** - prefix + object name

Object value는 body의 내용이다.

<br>

## Amazon S3 - Versioning

Amazon S3안에 있는 파일들을 버저닝할 수 있다.

버전 1부터 count

버킷 레벨에서도 가능

version enable로 하지 않으면 null로 표현

<br>

## Amazon S3

S3에 있는 object들을 암호화하는 4가지 방법(SSE(Server Side Encryption))

+ SSE-S3 : 각 객체는 고유한 키로 암호화
  + S3에서 관리
+ SSE-KMS : KMS의 이점을 활용하여 암호화 키를 관리
  + KMS에 의해 관리
  + 사용자가 key rotation policy를 전적으로 컨트롤할 수 있다.
+ SSE-C(고객 제공 암호화 키) : 자신의 암호화 키로 관리하고 싶을 때
  + Customer side에서 키 관리 (S3에서 키를 저장하지 않는다.)
  + encryption은 S3에서 동작
  + **HTTPS**를 무조건 사용해야 한다.
+ Client Side Encryption : S3로 보내기 전에 데이터를 암호화
  + 외부인이 S3를 trust하지 못할 때 사용
  + client는 그들 스스로 S3에 보내기 전에 data를 암호화해야 한다.

<br>

## S3 CORS

CORS(Cross-Origin Resource Sharing)은 한 도메인에 로드된 클라이언트 웹 응용 프로그램이 다른 도메인의 리소스와 상호 작용하는 방법을 정의한다.

만약 client가 S3 bucket에 cross-origin request를 보내면, 올바른 CORS headers를 가능하게 해야한다. 













