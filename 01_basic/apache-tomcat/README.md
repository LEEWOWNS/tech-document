* Web server 없이  WAS만 사용한다고 가정해보자.
  웹페이지에는 정적 데이터뿐만 아니라 동적 데이터도 함께 존재한다.
  
  Tomcat은 WAS Server이지만 WEB Server의 기능도 갖추고 있다.
  하지만 Tomcat의 Web server 기능은 Apache의 Web Server보다 느린 처리속도를 보였고, 
  Web의 모든 정적/동적 데이터를 모두 WAS가 처리한다면 결과적으로 사용자의 요청의 응답이 느려지게 될 것이다.
  때문에 정적 데이터는 Web Server Apache가 처리하고 동적 데이터는 WAS인 Tomcat이 
  처리함으로써 Server의 전체적인 부하를 분산하고 속도를 빠르게 하기 위해 연동을 해서 사용하는 것이다.
  
  지금은 Tomcat이 많이 발전해서 Tomcat의 Web Server가 Apache에 뒤쳐지지 않을 만큼의 기능을 하지만 
  그럼에도 불구하고 연동하는 이유는 Apache내에서만 설정할 수 있는 부분이라던가, 
  Apache에서 제공하는 유용한 모듈을 Tomcat에서는 사용할 수 없는 부분 등의 이유가 있다.
  
  즉, 각각 사용목적에 따라 용도가 다르다.
  HTML 파일이나 이미지와 같은 정적 컨텐츠들은 WAS까지 거칠 필요없이 Web Server만 
  통해서 바로 처리/응답 하는 것이 빠르다.
  Web Server와 WAS를 연동하여 각각의 역할 분담을 시켜, 
  요청에 대한 응답을 빠르고 효율적으로 처리하게 되는 것이다.
Apache - Tomcat 연동 동작 플로우
1. Apache Web Server의 httpd.conf에 Tomcat 연동을 위한 설정을 추가하고 
   Tomcat에서 처리할 요청을 지정

2. 사용자의 브라우저는 Apache Web Server에 접속하여 요청 ( 통상 80port )

3. Apache Web Server는 사용자의 요청이 들어왔을 때,
   이 요청이 Tomcat에서 처리되도록 지정된 요청인지 확인

4. Tomcat에서 처리해야 하는 경우 Apache Web Server Tomcat의 AJP포트 
   ( 통상 8009 port )에 접속해 요청을 Tomcat에게 전달

5. Tomcat은 Apache Web Server로 부터 요청을 받아 처리한 후, 
   처리 결과를 다시 Apache Web Server에게 돌려준다.

6. Apache Web Server Tomcat으로 전달받은 처리 결과를 사용자에게 전송한다.
AJP ( Apache JServ Protocol ) ?
웹서버(Apache)에서 받은 요청을 WAS로 전달해주는 프로토콜이다.
Apache HTTP Server, Apache Tomcat, 웹스피어, 웹 로직, JBOSS, JEUS 등 다양한 WAS에서 지원한다.
AJP 프로토콜은 중계 서버 또는 신뢰된 서버간의 서버 투 서버 통신에 많이 활용된다.
HTTP 보다 더 빠른 프로토콕 ( 바이너리 프로토콜 )
TCP Connection Pool의 사용( HTTP는 Stateless 프로토콜, Conection Pool을 구성해도 URI 한정 )
확장성 용이
