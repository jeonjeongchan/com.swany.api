# 챕터1. 인텔리제이로 스프링부트 시작하기

웹 서비스를 만들기 위해서 가장 첫번째로 해야 될일 : 개발환경 구성.<br>
대표적으로 이클립스, 인텔리제이가 있다.
스프링부트에서는 인텔리제이가 더 친숙하기 때문에 추천한다.

## 1.1 인텔리제이 소개
![인텔리제이](../img/1장/인텔리제이.jpg)<br>
이클립스에 비해 인텔리제이가 갖는 장점

````
* 강력한 추천 기능. 
* 더 다양한 리팩토링, 디버깅 기능.
* 이클립스의 깃에 비해 높은 자유도.
* 빠른 검색 속도와 업데이트.
* HTML과 CSS, JS XML에 대한 강력한 기능 지원.
````
등등이 있다.

실제로 네이버,카카오,라인,쿠팡,우아한형제 등등
이름만 들어도 유명 IT 회사들이 인텔리제이를 사용하고 있다.

## 1.2 인텔리제이 설치하기
#### 1.2.1. 툴박스 내려받기
툴박스란?<br>
<br>
![툴박스](../img/1장/툴박스.png)
![툴박스](../img/1장/툴박스1.png)
````
젯브레인 제품 전체를 관리 해주는 데스크.
화면에서 free download 클릭
````
<http://www.jetbrains.com/toolbox/>
#### 1.2.2. 툴박스 실행화면
````
IntelliJ IDEA Community -> install
````
#### 1.2.3. 인텔리제이 JVM 옵션 설정
![툴박스](../img/1장/툴박스4.png)
````
Maximum heap dize : 750MB -> 4GB
````
## 1.3 인텔리제이 실행

#### 1.3.1. 툴박스 실행화면
````
인텔리제이 : 프로젝트, 모듈
이클립스 : 워크스페이스

인텔리제이는 한화면에 하나의 프로젝트만 불러올수있다.

처음 설치 할 경우에는 가져올 이전 설정이 없으므로
Do not import setting -> OK를 해주면 된다.
````
#### 1.3.2. 툴박스 설정
````
단축키 : default
런처 스크립트 설정 : 왼쪽누르고 next
시작 설정 스크립트 생성 : 그냥 next
플러그인 설정 : 기본설정이면 그냥 next
````
#### 1.3.3. 프로젝트 생성
````
모든 설정이 끝나면 프로젝트 생성 화면이 나온다.
프로젝트 유형 : gradle
GroupId, ArtifactId 이름 작성
gradle 옵션 : default
디렉토리 위치는 기본적으로 ArtifactId가 프로젝트 이름이 된다.
````

#### 1.4. gradle 프로젝트를 spring boot 프로젝트로 변경
````
build.gradle : 플러그인 의존성 관리 설정
repositories : 라이브러리들을 어떤 원격 저장소에서 받을지 정해준다.
mavenCentral, jcenter 2개를 많이 사용한다.
Enable Auto-import를 누르면 build.gradle이 변경될때마다 자동으로 반영된다.
오른쪽 상단 gradle 창을 이용하여 라이브러리가 잘 반영됬는지 확인을 한다. 
````
#### 1.5. 깃허브 사용하기
````
ctrl + shift + a = action창 ->
share project on Github 선택 후 엔터 ->
깃허브 로그인 ->
저장소 이름을 프로젝트이름으로 설정후 등록 ->
share 버튼 클릭 ->
.idea 디렉토리 제외하고 commit ->
push
````
#### 1.6. ignore 플러그인 설치
````
ctrl + shift + a ->
plugins 검색 ->
plugins action 선택 ->
marketplace탭에서 scala 설치 ->
.ignore 설치
주의!! 인텔리제이를 다시 시작해야만 설치한 플러그인이 적용이 된다.
alt + insert를 이용하여 생성목록 열기 ->
아래에 .ignore file -> gitignore file[git]을 선택 후 생성
이후 자동으로 생성되는 파일을 제외 시키고 싶으면
파일안에 코드를 추가 시켜주면된다.
````
# 챕터2. 스프링부트 테스트코드

## 2.1. 테스트 코드란?

HDD : 테스트가 주도하는 개발.

테스트코드를 작성하는 이유<br>

1. 기능 단위의 테스트 코드를 작성.
    ````
    * 개발단계 초기에 문제 발견을 도와줌.
    * 리팩토링하거나 라이브러리 업그레이드 등에서 
      기존 기능이 올바르게 작동하는지 확인시켜줌.
    * 기능에 대한 불확실성을 감소시켜줌.
    * 시스템에 대한 실제 문서를 제공.
    * 단위 테스트 자체가 문서로 사용가능.
    ````
2. System.our.println() 통해 눈으로 검증해야 하는 문제.<br>

     테스트 코드를 작성하면 자동검증이 가능.

3. 개발자가 만든 기능을 안전하게 보호.

    세가지 단계의 공통점 : 기존 기능이 잘 작동되는 것을 보장해준다.

    테스트 코드는 기술이자 습관을 길들이는 것이 중요하다.
````
가장 대중적인 테스트 프레임워크 : xUnit

JUnit - Java
DBUnit - DB
CppUnit - C++
NUnit - .net

java를 사용하므로 JUnit을 시용.
````
## 2.2. Hello Controller 테스트 하기

````
생성할 패키지 위치에 마우스 우클릭을 하여 new -> package 클릭
일반적으로 패키지명은 도메인 사이트 주소 역순으로 만들기.
패키지 생성을 하면 java class를 클릭하여 Application으로 생성.
주의!! 클래스 파일은 앞글자가 무조건 대문자이여야한다.
````

# 챕터6. AWS 서버 환경
외부에서 본인이 만든 서비스에 접근을 할려면??<br>

'24시간 작동하는 서버'가 필요하다.<br>
그중에서도 3가지 선택지가 있다.
````
* 집에 pc를 24시간 구동.
* 호스팅 서비스(cafe24)를 이용.
* 클라우드 서비스(AWS)를 이용.
````
호스팅 서비스와 집PC 이용하는것이 저렴하지만,<br>
트래픽이 몰리면 유동적으로 사양을 늘릴수있는<br>
클라우드 서비스가 유리하다.

* 클라우드란 ?
````
인터넷을 통해 서버, 스토리지, DB, 네트워크, 소프트웨어, 모니터링 등
컴퓨팅 서비스를 제공하는 것이다.
````

클라우드의 종류 <br>
하나 . Infrastructure as a Service(IaaS)
* 기존 물리 장비를 미들웽어와 함께 묶어둔 추상화 서비스.
* 가상머신, 스토리지, 네트워크 등 IT 인프라를 대여해주는 서비스.
* AWS의 EC2, S3.

둘 . Platform as a Service(PaaS)
* Iaas에서 한번 더 추상화 한 서비스.
* 많은 기능이 자동화 되어 있음.
* AWS의 Beanstalk, Heroku.

셋 . Software as a Service (SaaS)
* 소프트웨어 서비스.
* 구글드라이브, 드랍박스 등

AWS를 선택하는 이유
* 첫가입시 1년간 대부분 서비스가 무료.
* 기본적으로 지원하는 기능이 많아 개발에 더 집중할 수 있다.
* 많은 기업이 AWS를 사용한다.
* 자료와 커뮤니티가 활성화 되어있다. 
## 6.1. AWS 회원가입
AWS 사이트<br>
[https://aws.amazon.com/ko/](https://aws.amazon.com/ko/)

![1](../img/6장/1.png)

'무료 계정 만들기' 클릭

![2](../img/6장/2.png)

![3](../img/6장/3.png)

![4](../img/6장/4.png)

주소는 네이버 영문주소를 이용한다.<br>
입력하고 '(필수) 동의하고 계정 만들기' 클릭


![5](../img/6장/5.png)

![6](../img/6장/6.png)

결제를 해야된다. <br>
최소 1달러가 있어야된다.<br>
보안문자 입력하면 등록된 전화번호로 4자리 코드가 전달된다.
실제로는 청구가 안된다.

![7](../img/6장/7.png)

마지막으로 무료기본 플랜을 선택하면된다.

![8](../img/6장/8.png)

콘솔에 로그인

## 6.2. EC2 인스턴스 생성하기

EC2는 AWS에서 제공하는 성능, 용량 등을 유동적으로 사용할 수 있는 서버다.<br>
즉, AWS에서 리눅스, 윈도우를 사용합니다 라고 하면 EC2를 말하는 것이다.

무료 AWS의 제한<br>
* 사양이 t2.micro만 가능.
* vCPU(가상 CPU) 1 core, 메모리 1GB 사양.
* vCPU는 물리 CPU 상야의 절반 정보의 성능.
* 월 750 시간의 제한. 초과하면 비용 부과.<br>
    즉, 24시간 * 31일 = 744시간<br>
    1대의 t2.micro만 사용하면 된다.
    
![9](../img/6장/9.png)    
리전을 서울로 변경.

![10](../img/6장/10.png) 

변경을 하였으면 검색창에서 ec2를 입력.

![11](../img/6장/11.png)

인스턴스 시작 클릭.    

![12](../img/6장/12.png)

Amazon Linux AMI : 아마존 머신 이미지

EC2 인스턴스를 시작하는데 필요한 정보를 이미지를 만들어 둔것.

Amazon Linux AMI를 선택.

Amazon Linux AMI 2버전도 있지만 1버전을 선택한 이유 :

자료가 1이 더 많다.

센토스 AMI도 사용할수 있지만 아마존 AMI를 사용하는 이유 :

* 아마존이 개발을 하고 있어서 지원받기 쉬움.
* AWS의 각종 서비스와의 상성이 좋다.
* yum이 매우 빠르다.

![13](../img/6장/13.png)
프리티어로 표기된 t2.micro를 선택   
t2 : 요금 타입<br>
micro : 사양 <br>
t시리즈가 범용으로 불린다.

![14](../img/6장/14.png)
세부 정보 구성

별다른 설정 없이 next~
![15](../img/6장/15.png)
스토리지 선택

스토리지 : 저장공간 즉, 서버의 디스크 <br>
용량을 얼마나 정할지 선택하는 단계.
최대 30gb까지 가능.<br>
30gb적고 next

![16](../img/6장/16.png)
name 태그를 등록.
ec2의 이름을 붙인다고 생각하면 된다.

![17](../img/6장/17.png)
보안설정
원하는 보안 이름 적고, ip를 내 ip로 변경해준다.

![18](../img/6장/18.png)

인스턴스로 접근하기 위해서는 pem 키가 필요하다.<br>
일종의 마스터 키이므로 절대 유출을 하서는 안된다.<br>
잘 관리 할수 있는 디렉토리로 저장을 해야된다.<br>
기존에 생성된 pem 키가 있다면 선택하고<br>
없으면 신규로 생성합니다.
 
![19](../img/6장/19.png)

인스턴스 목록

여기서 생성중이거나 <br>
생성이 된 인스턴스를 확인 할수있다.

인스턴스도 하나의 서버이기 때문에 ip가 존재한다.<br>
인스턴스를 생성 하게되면 새 ip가 할당이 되는데<br>
같은 인스턴스를 중지하고 다시 시작해도
새 ip가 할당이 된다.<br>
그래서 pc에서 접근할때마다<br> ip주소를 확인해야된다.

![20](../img/6장/20.png)

AWS의 고정 IP를 Elastic IP, (탄력적 IP) 라고 불린다.

탄력적 IP를 선택하고 주소가 없으므로 <br>
그림과 같이 눌러준다.

![21](../img/6장/21.png)

![22](../img/6장/22.png)
그림과 같이 눌러준다.

그면 탄력적 IP가 발급이 된다.

![23](../img/6장/23.png)
완성된 탄력적 IP를 확인하고<br>
EC2주소와 탄력적 IP를 연결시켜줘야된다.<br>
연결을 해주자. 클릭.

![24](../img/6장/24.png)
인스턴스 와 프라이빗 IP주소를 선택해준다.

연결~

![25](../img/6장/25.png)

연결이 완료되면 왼쪽 카테고리에 있는 인스턴스 탭을 클릭해서<br>
다시 인스턴스 목록 페이지로 이동.

![26](../img/6장/26.png)

인스턴스를 누르고 우측 하단을 보면 <br>
퍼블릭 ip과 탄력적 ip가 같은지 확인을 하면 된다.

여기까지 하면 EC2 인스턴스 생성 과정은 끝났다.

주의 : 생성한 탄력적 IP는 생성하고 무조건 무조건<br>
EC2 서버에 연결을해야 비용이 청구가 안된다.
탄력적 IP는 혼자 두면 안된다.
정말 주의하자.

## 6.3. EC2 서버에 접속하기
* Mac & Linux = 터미널
* window = putty

오랜 시간 접속이 안되거나, 권한이 없어서 안된다고 메시지가 나오면..
1. HostName 값이 정확히 탄력적 IP로 되어있는지 확인.
2. EC2 인스턴스가 running 상태인지 확인.
3. EC2 인스턴스의 보안그룹 -> 인바운드 규칙에서 현재 본인의 IP가 등록되어 있는지 확인.

나는 window를 사용하기 때문에 윈도우만 작성한다.

putty 사이트에 들어간다. 

[https://www.putty.org/](https://www.putty.org/)

![27](../img/6장/27.png)

실행 파일은 두개.
* putty.exe
* puttygen.exe

![28](../img/6장/28.png)


putty는 pem 키로 사용이 안되며<br>
pem 키를 ppk 파일로 변환을 해야만 한다.
puttygen이 그역할을 해준다.

![30](../img/6장/30.png)

puttygen.exe 실행 모습

Conversions -> Import Key를 선택 -> <br>
내려받은 pem 키를 선택

![31](../img/6장/31.png)

![32](../img/6장/32.png)

자동으로 변환이 진행된다.

Save private Key 클릭.

![33](../img/6장/33.png)

경고메세지

![33](../img/6장/34.png)

ppk 파일이 저장될 위치와 ppk 이름을 등록.

생성이 됬으면 putty.exe 실행

![29](../img/6장/29.png)

putty.exe 실행 모습

* HostName : username@public_ip를 등록<br>
    ex2-user@탄력적 IP주소를 등록하면된다.
  
* port : ssh 접속 포트인 22를 등록.

* Connection type : SSH를 선택.


항목을 모두 채우고 왼쪽 사이드바에 있는 <br>
connection -> SSH -> Auth를 차례로 클릭.<br> 
ppk 파일을 로드할 수 있는 화면으로 이동.<br>
그다음 Browse... 버튼 클릭.

![35](../img/6장/35.png)

전에 생성한 ppk 파일 선택해서 불러오기.

![36](../img/6장/36.png)

그리고 Seesion 탭으로 이동하여 Saved Sessions에<br>
현재 설정들을 저장할 이름을 등록하고 save 버튼을 클릭.

![37](../img/6장/37.png)

저장한 뒤 open 버튼을 클릭하면 다음과 같이 SSH 접속 알림이 등장한다.<br>
yes~

![38](../img/6장/38.png)

ssh 접속 성공~

![39](../img/6장/39.png)

## 6.4. 아마존 리눅스 1 서버 생성 시 꼭 해야 될 설정들

아마존 리눅스 1인 경우 기본 자바 버전이 7이다.<br>
자바 8버전이 필요하니 8버전을 EC2에 설치해보자.

    * sudo yum install -y java-1.8.0-openjdk-devel.x86_64

설치가 완료되었다면 인스턴스의 java 버전을 8로 변경.

    * sudo /usr/sbin/alternatives --config java

선택화면이 나오면 2를 입력해주자.

버전이 변경되었으면 java7을 삭제한다.

    * sudo yum remove java-1.7.0-openjdk

그리고 현재버전을 확인해주자

    * java -version
    
타임존 변경

EC2 서버의 기본 타임존 : UTC<br>
한국과의 시간차 9시간<br>
한국시간으로 바꾸어보자.

    * sudo rm /etc/localtime
    * sudo ln -s /usr/share/zoneinfo/Asia/Seoul /etc/localtime
    
정상적으로 수행을 햇으면 KST로 바뀐것을 볼수있다.<br>
띄어쓰기 주의

Hostname 변경

여러 서버를 관리중이면 ip만으로 어떤 서비스의 서버인지 확인이 어렵다.
그것을 표현하기 위해서 HOSTNAME을 변경할 것이다.

    * sudo vim /etc/sysconfig/network
    
![40](../img/6장/40.png) 변경전
![41](../img/6장/41.png) 변경후
![42](../img/6장/42.png) 
잘나오는 모습이다.

Hostname이 등록이 되었다면 한가지 작업을 더해야 된다.<br>

다음 명령어로 /etc/hosts 파일을 열어 본다.
    
    sudo vim /etc/hosts
    
![43](../img/6장/43.png) 

com-swany 위에서 그림같이 등록을 해준다.

그리고 정상적으로 등록이 되었는지 밑에있는 명령어를 입력한다.
    
    curl 등록한 호스트 이름
    
![44](../img/6장/44.png)     

(7) Failed to connct to 이런 문장이 뜨면
등록에 성공한 것이다.<br>
즉, 80포트로 실행된 서비스가 없다는 뜻이고,<br>
curl 호스트 이름으로 실행이 잘 되었음을 의미한다.

# 챕터7. AWS RDS

AWS에 데이터베이스 환경을 만들어보자.<br>

직접 데이터베이스를 설치하지 않는다.

AWS에서 작업들을 모두 지원하는 관리형 서비스 <br>
RDS를 제공한다.

RDS : AWS에서 지원하는 클라우드 기반 관계형 데이터베이스.<br>
운영 작업을 자동화하여 개발자가 개발에 집중할 수 있게 지원하는 서비스. 

## 7.1. RDS 인스턴스 생성하기

AWS 사이트에서 rds를 입력해서 검색을한다.

![1](../img/7장/1.png)  

데이터 베이스 생성을 누른다. 

![2](../img/7장/2.png) 

그 다음 mariaDB를 선택

다른 DB를 사용해도 되지만 mariaDB를 추천하는 이유

    * 가격
    * Amazon Aurora 교체 용이성

RDS는 가격은 라이센스 비용 영향을 받는다.<br>
그래서 MySQL, mariaDB, PostgreSQL 이 중에서 고르는것을 추천.

Amazon Aurora는 다른 SQL에 비해서 월등한 성능을 제공한다. <br>
그리고 아마존에서 직접 엔지니어링을 하고 있는것이 큰 장점이다.
    
![3](../img/7장/3.png) 

프리 티어 선택

![4](../img/7장/4.png) 

자기가 편한 정보와 이름을 입력해준다.

![5](../img/7장/5.png) 

스토리지 설정

![6](../img/7장/6.png) 

추가 연결 구성에서 예로 변경.

![7](../img/7장/7.png) 

나머지 옵션은 그대로 동일하면 된다.

![8](../img/7장/8.png) 

생성~

![9](../img/7장/9.png) 

생성중~

![10](../img/7장/10.png) 

완성.

## 7.2. RDS 운영환경에 맞는 파라미터 설정.
 
    * 타임존
    * Character Set
    * Mac Connection
    
3가지 설정을 필수로 해야된다.

![11](../img/7장/11.png) 

파라미터 그룹 클릭

![12](../img/7장/12.png) 

파라미터 그룹 생성

![13](../img/7장/13.png) 

전에 10.2 설정했기때문에 10.2로 설정한다.

![14](../img/7장/14.png) 

설정이 완료되었다.

새로만든 파라미터 그룹을 보자.

![15](../img/7장/15.png) 

파라미터 편집을 해보자.

timezone 설정<br>
서울로 바꿔준다.

![17](../img/7장/17.png) 

![16](../img/7장/16.png) 





    * character_set_client
    * character_set_connection
    * character_set_databae
    * character_set_filesystem
    * character_set_results
    * character_set_server
    * collation_connection
    * collation_server

character은 utf8mb4로,<br>    
collation은  utf8mb4_general_ci로 변경한다.
    

![18](../img/7장/18.png) 

utf8 은 이모지를 저장x
utf8mb4는 이모지를 저장할수 있다.

![19](../img/7장/19.png)  이모지

Max connection 수정을 해준다.<br>
넉넉하게 150정도로

![20](../img/7장/20.png)

생성된 파라미터 그룹을 데이터베이스에 연결해보자.

![21](../img/7장/21.png) 

DB 파라미터 그룹은 default로 되어있다. <br>
방금만든 신규 파라미터 그룹으로 변경한다.

![22](../img/7장/22.png)

![23](../img/7장/23.png)

즉시 적용을 해준다.

예약으로 하게 되면 데이터베이스가 작동을 하지 않을수가 있다.
  
![24](../img/7장/24.png)

파라미터 그룹이 제대로 반영되지 않을때가 있기때문에 재부팅을 해준다.

## 7.3. 내 PC에서 RDS에서 접속해 보기

RDS 보안그룹에 본인 PC의 IP를 추가 해보자.

![25](../img/7장/25.png)

![26](../img/7장/26.png)

![27](../img/7장/27.png)

데이터베이스 -> 내가만든 db 클릭 -> <br>
보안 그룹 정보를 그대로 두고, 브라우저를 새로 엽니다.<br>
다른 브라우저 창에서 보안 그룹의 ID를 복사합니다.

![28](../img/7장/28.png)

![30](../img/7장/30.png)

![29](../img/7장/29.png)

복사한 보안 그룹 key와 본인의 IP를 RDS 보안 그룹의 인바운드로 추가합니다.

완성 됬으면 로컬에서 한번 테스트 ㄱㄱ

![31](../img/7장/31.png)

엔드포인트 복사

![32](../img/7장/32.png)

database Navigator 설치 하고 재시작.

ctrl + shift + a  Action창이뜬다.

![33](../img/7장/33.png)


![34](../img/7장/34.png)

mySQL 선택

![35](../img/7장/35.png)

기입하고 test해서 successful이 뜨면 ok.

![36](../img/7장/36.png)

클릭.

![37](../img/7장/37.png)

신규 콘솔창 생성.

![38](../img/7장/38.png)

내가 생성한 RDS명이다.

![39](../img/7장/39.png)

실행.

![39](../img/7장/40.png)

주의 드래그를 해서 실행버튼을 누르자

![39](../img/7장/41.png)

성공적으로 수행됬다.

![39](../img/7장/42.png)

![39](../img/7장/43.png)

character_set, collation 설정 확인

하지만 latin1로 되어있는모습이 보인다.

변경해보자.

![44](../img/7장/44.png)

![45](../img/7장/45.png)

![46](../img/7장/46.png)
![47](../img/7장/47.png)

성공적으로 utf8mb4로 잘바뀌었다.

![48](../img/7장/48.png)
![49](../img/7장/49.png)

타임존도 한국시간으로 잘바뀌었다.

![50](../img/7장/50.png)
![51](../img/7장/51.png)

잘나온다.

주의 사항 쿼리문 전체드래그 하지말고,<br>
내가 실행할 부분만 드래그해서 실행해야된다.

ex) select문이면 select문만 insert문이면 insert문만 드래그해서 실행.


## 7.4. EC2에서 RDS로 접근 확인

putty.exe 실행

mysql CLI를 설치.

    * sudo yum install mysql
    
![52](../img/7장/52.png)

설치완료.

![53](../img/7장/53.png)

![54](../img/7장/54.png)

비밀번호까지 치면 접속이 된다.

![54](../img/7장/55.png)

끝~    
    
# 챕터8. EC2 서버에 프로젝트 배포해보기.

전에 배운 것을 조합 실제 서비스를 배포해보자.

## 8.1. EC2에 프로젝트 Clone 받기

EC2에 깃 설치.

    * sudo yum install git
    
설치가 완료 됬으면 버전 확인.

    * git --version

git clone으로 프로젝트를 저장할 디렉토리를 생성.

    * mkdir ~/app && mkdir ~/app/step1
    
생성된 디렉토리로 이동

    * cd ~/app/step1
 
![1](../img/8장/1.png)

깃허브 웹페이지 주소 복사.

    * git clone 복사한 주소
    
EC2에 복사한 주소 붙여넣기 방법 : 마우스 우클릭

완료 되었으면 확인.

    * cd 프로젝트명
      ll
   
![2](../img/8장/2.png)    

프로젝트 코드들이 모두 있다. 

코드들이 잘 수행이 되는지 테스트로 검증.

    ./gradlew test   
    
만약 테스트가 실패해서 수정하고 깃허브에 푸시를 했다면
<br>
프로그램 폴더 안에 명령어를 사용.
    
    git pull
    
gradlew 실행 권한이 없다는 메세지가 뜨면

    -bash: ./gradlew: Permission denied
    
다음 명령어로 실행 권한을 추가한 뒤 다시 테스트를 수행하면 됩니다.

    chmod +x ./gradlew
    
ec2 git 디렉토리에 파일을 잘못 넣는 경우 ec2 디렉토리 지우는법

    
    rm -rf 삭제하고자 하는 디렉토리명
    
    중요!! 상위폴더에서 지우기

권한이 안되는 경우

    root    ALL=(ALL)    ALL
    
    ec2-user    ALL=(ALL) ALL
    
세팅을 다하고 다시 테스트를 실행을 하면

![3](../img/8장/3.png)   

성공적으로 테스트완료.

## 8.2. 배포 스크립트 만들기

배포 : 작성한 코드를 실제 서버에 반영하는 것.

    * git clone 혹은 git pull을 통해 새 버전의 프로젝트 받음
    
    * gradle이나 maven을 통해 프로젝트 테스트와 빌드.
    
    * EC2 서버에서 해당 프로젝트 실행 및 재실행.
    
배포할 때마다 개발자 하나하나 명령어를 실행하는 것은 불편함이 많았다.

쉘 스크립트를 이용해 스크립트만 실행 해보자.

확장자 : .sh

리눅스에서 기본은 사용 가능.

빔 : GUI(마우스 환경) 가 아닌 환경에서 사용할 수있는 도구.
                
~/app/step1/에 deploy.sh 파일을 하나 생성

    vim ~/app/step1/deploy.sh        
    
빔 사용법

    #!/bin/bash
    
    REPOSITORY=/home/ec2-user/app/step1
    PROJECT_NAME=com.swany.api
    
    cd $REPOSITORY/$PROJECT_NAME/
    
    echo "> Git Pull"
    
    git pull
    
    echo "> 프로젝트 Build 시작"
    
    ./gradlew build
    
    echo "> step1 디렉토리로 이동"
    
    cd $REPOSITORY
    
    echo "> Build 파일 복사"
    
    cp $REPOSITORY/$PROJECT_NAME/build/libs/*.jar $REPOSITORY/
    
    echo "> 현재 구동중인 애플리케이션 pid 확인"
    
    CURRENT_PID=$(pgrep -f ${PROJECT_NAME}*.jar)
    
    echo "현재 구동 중인 애플리케이션 pid: $CURRENT_PID"
    
    if [ -z "$CURRENT_PID" ]; then
            echo "> 현재 구동 중인 애플리케이션이 없으므로 종료하지 않습니다."
    else
            echo "> kill -15 $CURRENT_PID"
            kill -15 $CURRENT_PID
            sleep 5
    fi
    
    echo "> 새 애플리케이션 배포"
    
    JAR_NAME=$(ls -tr $REPOSITORY/ | grep *.jar | tail -n 1)
    
    echo "> JAR Name : $JAR_NAME"
    
    nohup java -jar $REPOSITORY/$JAR_NAME 2>&1 &


1.  REPOSITORY=/home/ec2-user/app/step1
    
    * 프로젝트 디렉토리 주소를 변수로 저장.
    
    * 프로젝트 이름도 동일한 방법으로 저장.
    
    * 쉘에서는 타입 없이 저장가능.
    
    * 쉘에서는 $ 변수명으로 변수를 사용할 수 있음.

2. cd $REPOSITORY/$PROJECT_NAME/

    * 제일 처음 git clone 받았던 디렉토리로 이동.
    
    * 바로 위의 쉘 변수 설명을 따라 /home/ec2-user/app/step1/com.swany.api(프로젝트이름) 주소로 이동.
    
3. git pull

    * 디렉토리 이동 후, master 브랜치의 최신 내용을 받습니다..
    
4. ./gradlew build

    * 프로젝트 내부의 gradlew로 build를 수행합니다.
    
5. cp./build/libs/*.jar $REPOSITORY/

    * build의 결과물인 jar 파일을 복사해 jar 파일을 모아둔 위치로 복사.
    
6. CURRENT_PID=$(pgrep -f springboot-webservice)

    * 기존에 수행 중이던 스프링 부트 애플리케이션을 종료합니다.
    
    * pgrep은 process id만 추출하는 명령어입니다.
    
    * -f 옵션은 프로세스 이름으로 찾습니다.
    
7. if ~ else ~ fi
    
    * 현재 구동 주인 프로세스가 있는지 없는지를 판단해서 기능을 수행합니다.
    
    * process id 값을 보고 프로세스가 있으면 해당 프로세스를 종료합니다.
    
8. JAR_NAME=$(ls -tr $REPOSITORY/ | grep *.jar | tail -n 1)

    * 새로 실행할 jar 파일명을 찾습니다.
    
    * 여러 jar 파일이 생기기 때문에 tail -n로 가장 나중의 jar 파일(최신 파일)을 변수에 저장합니다.
    
9. nohup java -jar $REPOSITORY/$JAR_NAME 2>&1 &    
        
    * 찾은 jar 파일명으로 해당 jar 파일을 nohup으로 실행합니다.
    
    * 스플링 부트의 장점으로 특별히 외장 톰캣을 설치할 필요가 없다.
    
    * 내장 톰캣을 사용해서 jar 파일만 있으면 바로 웹 애플리케이션 서버를 실행할 수 있습니다.
    
    * 일반적으로 자바를 실행할 때는 java -jar라는 명령어를 사용하지만, 이렇게 하면 사용자가 터미널 접속을 끓을 때 애플리케이션도 같이  애플리케이션도 같이 종료됩니다.
    
    * 애플리케이션 실행자가 터미널을 종료해도 애플리케이션은 계속 구동될 수 있도록 nohup 명령어를 사용합니다.
    

스크립트 실행 권한 추가.

    chmod +x ./deploy.sh
    
x 권한 추가 확인. 

스크립트 실행.

    ./deploy.sh
    
![4](../img/8장/4.png)    


nohup.out 파일 열기

    vim nohup.out
    
ClientRegistrationReopsitory를 찾을수없다고 에러 발생.

##8.3 외부 Security 파일 등록하기
    ClientRegistrationReopsitory를 생성하려면 clientId, clientSecret가 필수.
    
    git에서 제외 대상이면 ec2에서 직접 넣어주자.
    
app 디렉토리에 properties 파일 생성
    
    vim /home/ec2-user/app/application-oauth.properties
    
application-oauth.properties 로컬에 있는것을 복사해서 붙여넣기

application-oauth.properties 파일을 쓰도록 deploy.sh 수정
    
    ...
    nohup java -jar \
            -Dspring.config.location=classpath:/application.properties,/home/ec2-user/app/application-oauth.properties \
                $REPOSITORY/$JAR_NAME 2>&1 &
                
   
주의 : 띄어쓰기, 다음줄에 입력시 신중하게 작성을 해야된다.         

![5](../img/8장/5.png)       

정상적으로 실행 됬다.

##8.4 스프링 부트 프로젝트로 RDS 접근하기.

마리아DB에서 스프링부트 프로젝트 실행 하기 위한 작업.
    
    * 테이블 생성 : 직접 쿼리 이용.
    
    * 프로젝트 설정 : 드라이버 추가.
    
    * EC2 설정 : 접속 정보 보호.
 
RDS 테이블 생성

JPA가 사용될 엔티티 테이블.<br>
스프링 세션이 사용될 테이블.<br>
2가지 생성.

deploy.sh를 실행하고

vim nohup.out를 열어보면 posts와 user가 있다.

복사하여 RDS에 반영하자.

![6](../img/8장/6.png)  

스프링 세션 테이블 생성

intelliJ에서 Ctrl+Shift+N으로 schema-mysql.sql 파일 검색 
    
    CREATE TABLE SPRING_SESSION (
    	PRIMARY_ID CHAR(36) NOT NULL,
    	SESSION_ID CHAR(36) NOT NULL,
    	CREATION_TIME BIGINT NOT NULL,
    	LAST_ACCESS_TIME BIGINT NOT NULL,
    	MAX_INACTIVE_INTERVAL INT NOT NULL,
    	EXPIRY_TIME BIGINT NOT NULL,
    	PRINCIPAL_NAME VARCHAR(100),
    	CONSTRAINT SPRING_SESSION_PK PRIMARY KEY (PRIMARY_ID)
    ) ENGINE=InnoDB ROW_FORMAT=DYNAMIC;
    
    CREATE UNIQUE INDEX SPRING_SESSION_IX1 ON SPRING_SESSION (SESSION_ID);
    CREATE INDEX SPRING_SESSION_IX2 ON SPRING_SESSION (EXPIRY_TIME);
    CREATE INDEX SPRING_SESSION_IX3 ON SPRING_SESSION (PRINCIPAL_NAME);
    
    CREATE TABLE SPRING_SESSION_ATTRIBUTES (
    	SESSION_PRIMARY_ID CHAR(36) NOT NULL,
    	ATTRIBUTE_NAME VARCHAR(200) NOT NULL,
    	ATTRIBUTE_BYTES BLOB NOT NULL,
    	CONSTRAINT SPRING_SESSION_ATTRIBUTES_PK PRIMARY KEY (SESSION_PRIMARY_ID, ATTRIBUTE_NAME),
    	CONSTRAINT SPRING_SESSION_ATTRIBUTES_FK FOREIGN KEY (SESSION_PRIMARY_ID) REFERENCES SPRING_SESSION(PRIMARY_ID) ON DELETE CASCADE
    ) ENGINE=InnoDB ROW_FORMAT=DYNAMIC;
    
복사하여 RDS에 반영하기.

프로젝트 설정

Maria DB 드라이버 build.gradle 등록.
    
    compile("org.mariadb.jdbc:mariadb-java-client")
        
application-real.properties resource 디렉토리에 추가.
    
    spring.profiles.include=oauth,real-db
    spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL5InnoDBDialect
    spring.session.store-type=jdbc
    
완료가 되었으면 깃허브로 푸쉬.

EC2 설정

app 디렉토리에 application-real-db.properties 파일을 생성합니다.
    
    vim ~/app/application-real-db.properties
    
* 내용추가
   
    
    spring.jpa.hibernate.ddl-auto=none
    spring.datasource.url=jdbc:mariadb://com-swany.caxeujmlufgo.ap-northeast-2.rds.amazonaws.com:3306/com_swany
    spring.datasource.username=jeon
    spring.datasource.password=Wkdlzhvl159
    spring.datasource.driver-class-name=org.mariadb.jdbc.Driver

deploy.sh가 real profile을 쓸수 있도록 수정.
    
    nohup java -jar \
             -Dspring.config.location=classpath:/application.properties,/home/ec2-user/app/application-oauth.properties,/home/ec2-user/app/application-real-db.properties \
            -Dspring.profiles.active=real \
            $REPOSITORY/$JAR_NAME 2>&1 &
        
deploy.sh를 실행해서 nohup.out 파일을 열어서 포트번호가 보이면 성공.
    
    입력하여 html 코드가 보이면 성공.
    
    curl localhost:8080  
    
##8.5 EC2에서 소셜 로그인하기

aws 보안 그룹변경

![7](../img/8장/7.png) 

aws EC2 도메인으로 접속

왼쪽 사이드바 '인스턴스' 메뉴를 클릭. <br>
EC2 인스턴스를 선택하면 퍼블릭 DNS를 확인할 수 있음.

![8](../img/8장/8.png) 

8787을 붙여서 브라우저에 입력하기.

![9](../img/8장/9.png) 

도메인을 가진 서비스가 되었지만 구글과 네이버 로그인이 안된다.<br>
둘다 등록을 해보자.

![10](../img/8장/10.png) 

![11](../img/8장/11.png)
 
![12](../img/8장/12.png) 

![13](../img/8장/13.png) 

네이버도 똑같이 네이버 api 설정을 찾아가서 url을 추가해주면 된다.

# 챕터9. Travis CI 배포 자동화

병합되고, 테스트를 수행할때 자동으로 배포를 하는 환경을 안만들어주면 실수할 여지가 많아진다. <br>
보완을 해보자.

## 9.1 CI & CD 소개
CI (지속적 통합) : VCS 시스템에 (git) 푸쉬를 하게되면 자동으로 테스트와 빌드가 수행되어 안정적인 배포파일을 만드는 과정.

CD (지속적 배포) : 빌드 결과를 자동으로 운영 서버에 무중단 배포까지 진행되는 과정.

CI 규칙 4가지
   
    * 모든 소스가 살아 있고, 누구든 현재의 소스에 접근할 수 있는 단일지점을 유지.
    
    * 빌드 프로세스를 자동화해서 누구든 소스로부터 시스템을 빌드하는 단일 명령어를 사용할 수 있게 할 것.
    
    * 테스팅을 자동화해서 단일 명령어로 언제든지 시스템에 대한 건전한 테스트 수트를 실행할 수 있게 할 것.
    
    * 누구나 현재 실행 파일을 지금까지 가장 완전한 실행 파일을 얻었다는 확실을 하게 할 것.
    
제일 중요한 것 '테스팅 자동화'

## 9.2 Travis CI 연동하기

Travis CI

무료서비스.

https://travis-ci.org/ 클릭

로그인 -> 계정명 -> settings 클릭

![1](../img/9장/1.png) 

상태바 활성화.

![2](../img/9장/2.png) 

그리고 활성화된 저장소 이름을 클릭.

![3](../img/9장/3.png) 

Travis CI 웹사이트에서 설정 끝.

프로젝트 설정

.travis.yml 파일로 한다.

yml 파일 확장자 : YAML

YAML : JSON에서 괄호를 제거 한 것.<br>
읽기 쉽게 하기 위해서 사용.

build.gradle와 같은 위치에서 .travis.yml 파일 생성

작성.
    
    language: java
    jdk:
      - openjdk8
    
    branches:
      only:
        - master
        
    # Travis CI 서버의 Home
    cache:
      directroles:
        - '$HOME/.m2/repository'
        - '$HOME/.gradle'
    
    script: "./gradlew clean build"
    
    # CI 실행 완료 시 메일로 알람
    notifications:
      email:
        recipients:
          - 본인 메일 주소
        
작성 후 master 브랜치에 커밋, 푸쉬

추가

![4](../img/9장/4.png) 

해결

![5](../img/9장/5.png)       

추가해준다.  

![6](../img/9장/6.png)   

![7](../img/9장/7.png)  

![8](../img/9장/8.png)     

## 9.3 Travis CI와 AWS S3 연동하기

S3 : AWS에서 제공하는 일종의 파일 서버.<br>
주로 이미지 파일을 업로드 할때 사용.

Travis CI 연동 구조

![9](../img/9장/9.png)

실제 배포는 AWS CodeDeploy 서비스를 이용.


AWS Key 발급

접근 가능한 권한을 가진 KEY를 생성해서 사용해보자.

IAM : AWS에서 제공하는 서비스의 접근 방식과 권한을 관리한다.

AWS에서 IAM 검색후

![10](../img/9장/10.png)

사용자 -> 사용자 추가 누르기

![11](../img/9장/11.png)

이름과 엑세스 유형 선택

권한 설정 방식은 기존 정책 직접 연결을 선택.

![12](../img/9장/12.png)

![13](../img/9장/13.png)

![14](../img/9장/14.png)

태그는 이름 알아볼수있게 정해준다.

![15](../img/9장/15.png)

잘 작성했는지 확인.

![16](../img/9장/16.png)

완료가 되면 엑세스 키와 비밀 엑세스 키가 생성이 됬다.
     
![17](../img/9장/17.png)

키등록

Travis CI의 설정 화면으로 이동   

![18](../img/9장/18.png)

Environment Variables 이 항목에서

AWS_ACCESS_KEY, AWS_SECRET_KEY를 변수로 해서 IAM 사용자에서 발급받은 키 값들을 등록한다.

    AWS_ACCESS_KEY : 엑세스 키ID
    AWS_SECRET_KEY : 비밀 엑세스 키

![19](../img/9장/19.png)  

![20](../img/9장/20.png)

등록을 했으면 .travis.yml에서 사용할 수 있다.

S3버킷 생성  

![21](../img/9장/21.png)
 
![22](../img/9장/22.png)

검색하고 버킷 만들기 클릭

![23](../img/9장/23.png)

버킷이름 짓기

![24](../img/9장/24.png)

별다른 설정없이 다음

![25](../img/9장/25.png)

모든 엑세스 차단 설정

![26](../img/9장/26.png)

생성된 모습.

.travis.yml 추가

    '''
    before_deploy:
      - zip -r com.swany.api *
      - mkdir -p deploy
      - mv com.swany.api.zip deploy/com.swany.api.zip
    
    deploy:
      - provider: s3
        access_key_id: $AWS_ACCESS_KEY # Travis repo settings에  설정된 값
    
        secret_access_key : $AWS_SECRET_KEY # Travis repo settings에 설정된 값
    
        bucket: com.swany.build # S3 버킷
        region: ap-northeast-2
        skip_cleanup: true
        acl: private # zip 파일 접근을 private으로
        local_dir: deploy # before_deploy에서 생성한 디렉토리
        wait-until-deployed: true
        
추가

전체 코드

    language: java
    jdk:
      - openjdk8
    
    branches:
      only:
        - master
    
    # Travis CI 서버의 Home
    cache:
      directroies:
        - '$HOME/.m2/repository'
        - '$HOME/.gradle'
    
    script: "./gradlew clean build"
    
    before_install:
      - chmod +x gradlew
    
    before_deploy:
      - zip -r com.swany.api *
      - mkdir -p deploy
      - mv com.swany.api deploy/com.swany.api
    
    deploy:
      - provider: s3
        access_key_id: $AWS_ACCESS_KEY # Travis repo settings에  설정된 값
    
        secret_access_key : $AWS_SECRET_KEY # Travis repo settings에 설정된 값
    
        bucket: com-swany-build # S3 버킷
        region: ap-northeast-2
        skip_cleanup: true
        acl: private # zip 파일 접근을 private으로
        local_dir: deploy # before_deploy에서 생성한 디렉토리
        wait-until-deployed: true
    
    # CI 실행 완료 시 메일로 알람
    notifications:
      email:
        recipients:
          - junjungchan@naver.com
          
다 됬으면 푸쉬~
 
![27](../img/9장/27.png)

![28](../img/9장/28.png)   

잘된 모습이다. 

![29](../img/9장/29.png)  

S3 버킷 모습

(zip 확장자를 뺏더니 압축파일 모양은 아니다.
추후 다시 해보기.)

## 9.4 Travis CI와 AWS S3, CodeDeploy 연동하기

EC2에 IAM 역할 추가하기

IAM 검색 -> 역할 -> 역할 만들기

![30](../img/9장/30.png)  

IAM 사용자와 역할의 차이

    역할
        
        * AWS 서비스에만 할당할 수 있는 권한
        * EC2, CodeDeploy, SQS 등
        
    사용자
    
        * AWS 서비스 외에 사용할 수 있는 권한
        * 로컬 PC, IDC 서버등
        
EC2에 사용할 역할 권한을 만들어보자.

AWS 서비스 -> EC2 선택        

![31](../img/9장/31.png)

EC2RoleFOrA 검색하여  AmazonEC2RoleforAWSCodeDeploy를 선택  

![32](../img/9장/32.png)      

그 다음 태그 이름은 마음대로 정해도 되지만 책에 있는 이름대로 지어보자.   
    
![33](../img/9장/33.png)          

![34](../img/9장/34.png) 

역할을 만들었으면 EC2 서비스에 등록 해보자.

EC2 인스턴스 목록 -> 본인의 인스턴스를 마우스 오른쪽 버튼 클릭 ->
인스턴스 설정 -> IAM 역할 연결/바꾸기 차례대로 선택

![35](../img/9장/35.png)  

방금 만든 역할을 선택.

![36](../img/9장/36.png) 

선택 완료하면 재부팅.

![37](../img/9장/37.png) 


CodeDeploy 에이전트 설치

EC2에 접속해서 다음 명령어를 입력.

    aws s3 cp s3://aws-codedeploy-ap-northeast-2/latest/install . --region ap-northeast-2

    띄어쓰기 주의
    
![38](../img/9장/38.png)     

이 메세지가 뜨면 성공.

install 파일 실행 권한 추가.

    chmod +x ./install

install 파일로 설치를 진행.

설치가 끝났으면 Agent가 정상적으로 실행되고 있는지 상태 검사.

    sudo service codedeploy-agent status
    
![39](../img/9장/39.png)      

이렇게 뜨면 정상.

CodeDeploy를 위한 권한 생성.

EC2에 접근할려면 권한 필요.

IAM 역할을 생성.

AWS 서비스 -> CodeDeploy 선택.

![40](../img/9장/40.png)

![41](../img/9장/41.png)

![41](../img/9장/42.png)

권한이 하나뿐이라 그냥 다음 누르면 된다.

![43](../img/9장/43.png)

완료.

CodeDeploy 생성

배포 삼형제

    Code Commit
        
        * 깃허브과 같은 코드 저장소 역할을 한다.
        * 깃허브에서 무료로 프라이빗 지원을 하고 있어서 거의 사용x
        
    Code Bild
    
        * 빌드용 서비스
        * 규모가 있는 서비스에서 대부분 젠킨스/팀시티를 사용해 거의 사용x
        
    CodeDeploy
    
        * AWS의 배포 서비스.
        * 대체재가 없다.
        * 많은 배포 기능을 지원한다.
        
Code Commit의 역할 : 깃허브

Code Build의 열할 : Travis CI

남은 CodeDeploy 서비스를 추가하면 삼형제 완성.

CodeDeploy 서비스 -> 애플리케이션 생성  

![44](../img/9장/44.png)  

![45](../img/9장/45.png) 

입력하고 생성.

그리고 배포 그룹 생성 버튼 클릭.

![46](../img/9장/46.png) 

![47](../img/9장/47.png) 

![48](../img/9장/48.png)

![49](../img/9장/49.png) 

![50](../img/9장/50.png)

1대 서버이니 전체 배포 옵션 선택.

Travis CI, S3, CodeDeploy 연동

S3에서 넘겨줄 zip 파일을 저장할 디렉토리를 하나 생성.

    mkdir ~/app/step2 && mkdir ~/app/step2/zip
    
Travis CI의 Build가 끝나면 S3에 zip 파일이 전송되고, 이 zip 파일은 / home/ec2-user/app/step2/zip로 복사되어 압축을 풀 예정이다.

Travis CI의 설정은 .travis.yml으로 진행.

AWS CodeDeploy의 설정은 appspec.yml로 진행. 

appspec.yml 파일 생성하고 작성.

    version: 0.0
    os: linux
    files:
      - source: /
        destination: /home/ec2-user/app/step2/zip/
        overwrite: yes
        
.travis,yml CodeDeploy 내용 추가.

    deploy:
        ...
    
    - provider: codedeploy
      access_key_id: $AWS_ACCESS_KEY # Travis repo settings에 설정된 값
      secret_access_key: $AWS_SECRET_KEY # Travis repo settings에 설정된 값
      
      bucket: com-swany-build # S3 버킷
      key: com.swany.api.zip # 빌드 파일을 압축해서 전달
      
      bundle_type: zip # 압축 확장자
      application: com.swany.api # 웹 콘솔에서 등록한 CodeDeploy 애플리케이션
      
      deployment_group: com.swamy.api-group # 웹콘솔에서 등록한 CodeDeploy 애플리케이션
      
      region: ap-northeast-2
      wait-until-deployed: true          