# 🐳 Docker 개요

## Docker란? 
- 어플리케이션을 패키징하는 툴
- 컨테이너라고 불리는 하나의 작은 소프트웨어 유닛 안에 Application + System Tools + 환경설정 + Dependencies -> 하나로 묶어 다른 서버, 다른 PC로 쉽게 배포하고 안정적으로 구동할 수 있게 도와주는 Tool
- 예시로 Node.js 개발한 코드를 서버에 배포 시, 가끔 내 PC와 서버의 node 버전이 달라 에러가 나는 경우도 있는데, 이를 해결하기 위해 Docker가 탄생
- Docker 컨테이너 안에는 개발한 Application을 정상적으로 동작하기 위한 Node.js. 환경 설정 npm, 여러 라이브러리들의 Dependencies, Application에 필요한 다양한 리소스들이 포함 -> Application에 구동해야 할 모든 것들을 Docker 컨테이너 안에 담았다!

![image](https://user-images.githubusercontent.com/30613069/156108752-b61824d3-60f2-447a-906f-5e1b5149b296.png)

<br/>

## VM vs Docker Container 차이점?
- VM : 하드웨어 Infrastructure + Virtual Box와 같은 소프트웨어를 이용해 각각의 가상머신을 만들 수 있는데, 한 운영체제(OS) 위에서 동일한 어플리케이션을 각각의 고립된 다른 환경에서 구동하기 위해서 VM을 이용해 어플리케이션을 구동해야 했음->  VM은 각각의 운영체제를 포함하고 있기 때문에 굉장히 무거움(운영체제 Infrastructure을 많이 잡아먹는 범인이 될 수도 있음)

![image](https://user-images.githubusercontent.com/30613069/156108767-cc9385e4-36b0-42cd-80e4-4cc8e9ed9ac9.png)

<br/>

- Container : VM의 경량화 버전. Container 는 무거운 OS를 포함하지 않고, Host OS를 공유함. (운영체제와 커널 공부하기)
- Container 를 운영하기 위해선 Container Engine이 필요하고, Container Engine이 Host OS에 접근해 필요한 것들을 처리 
- Container Engine 중 가장 많이 사용 되는 것이 Docker! 

![image](https://user-images.githubusercontent.com/30613069/156108792-ca4ee95a-f578-4b0e-b992-82d9998ea14f.png)

<br/>

## 🚍 Container 만들기 !
1. Dockerfile
	- Container를 어떻게 만들어야 하는지 설명서.  
	- Copy files :  우리 Application을 구동하기 위해서 꼭 필요한 파일들은 어떤 것인지?
	- Install Dependencies : 어떤 프레임워크나 외부 라이브러리를 설치해야 되는 지?
	- Set Environment variables : 필요한 환경 변수
	- Run setup scripts : 어떻게 구동해야 되는지 스크립트도 포함.
	
	<br/>

2. Image
	- 위에서 작성한 Docker 파일을 이용해 이미지를 만들 수 있음
	- Image 안에는 Application을 실행하는데 필요한 코드, 런타임 환경, 시스템 툴, 시스템 라이브러리 등 모든 세팅들이 포함되어 있음.
	- 실행 중인 상태를 순간 찰칵! 스냅샷으로 찍어서 이미지로 만들어 둔다라고 생각하면 됨.
	- 이렇게 만들어진 이미지는 변경이 불가능한 불변의 상태로 볼 수 있음.
	
	![image](https://user-images.githubusercontent.com/30613069/156108814-788e3c98-935c-48ee-bea2-909340a2be49.png)
	 
	<br/>

3. Container
	- 샌드박스처럼 우리가 잘 캡쳐해둔 Application의 이미지를 고립된 환경에서 개별적인 그 파일 시스템 안에서 실행할 수 있는 것을 말함.
	- Container 는 이미지를 이용해 우리 Application이 구동하게 됨.

![image](https://user-images.githubusercontent.com/30613069/156108825-e5f182b4-386a-4846-a921-737f141b7a31.png)

<br/>

##  ⛵ Container 배포하기
- 내 로컬 PC에서 Image를 작성하고, 깃헙과 같은 Container Registry에 내가 만든 Image를 PUSH를 하고, 필요한 서버나 또는 다른 개발자 PC에서 내가 만들어 둔 Image를 PULL해 그걸 그대로 실행하면 됨.
- Public : Docker hub, Red Hat, GitHub
- Private : Amazon, MS, Google

출처 : https://www.youtube.com/watch?v=LXJhA3VWXFA 도커 한방에 정리 🐳 (모든 개발자들이 배워보고 싶어 하는 툴!) + 실습 (드림코딩 by 앨리 ) 
	

