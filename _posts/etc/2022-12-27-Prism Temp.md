---
title:  "[TodoList] 나만의 프로그래밍 로드맵 (추가 중)" 

categories:
  - TodoList
tags:
  - [Programming, TodoList]

toc: true
toc_sticky: true

date: 2022-09-20
last_modified_at: 2022-10-25
---

1. FQDN (Fully Qualified Domain Name)
- 전체 도메인 네임
- 도메인 전체 이름을 표기하는 방식을 의미 | 호스트와 도메인을 함께 명시하여 전체 경로를 모두 표기하는 것
- 전체 주소 도메인 네임의 레이블의 계층
  ￼
- 예제
    - www.naver.com
        - www -> host
        - naver.com -> domain

(2, 3번은 Mobile 관련 글로 한번에)
2. IMEI (International Mobiold Equiment Identity)
- 국제 휴대전화기 고유 식별 번호
- 15자리로 이루어진 고유 식별 번호

3. ICCID (Integrated Circuit Card Identifier)
- SIM 카드의 고유 일련번호
- ICCID의 형식
    - MMCC IINN NNNN NNNN NN Cx
        - MM : 상수
        - CC : 국가코드
        - II : 발급자 식별자
        - N{12} : 계정 ID(“SIM 번호”)
        - C : Luhn 알고리즘을 사용하여 다른 19자리에서 계산된 Check Sum
        - x : 여분의 20번째 숫자가 ‘AT! ICCID?’에 의해 반환된다. 명령이지만 공식적으로 ICCID의 일부는 아니다.

4. Stanza
- XML 스트림을 통해 한 엔티티에서 다른 엔티티로 전송되는 구조화된 정보의 개별 의미 단위
- 원하는 정보를 전달하기 위해 필요에 따라 하위 요소(accompanying attributes, elements, and XML character data)를 포함할 수 있다.


5. TLS (Transport Layer Security)
- 컴퓨터 네트워크에 통신 보안을 제공하기 위해 설계된 암호 규약
- TCP/IP 네트워크를 사용하는 통신ㄴ에 적용되며, 통신 과정에서 전송 계층 종단간 보안과 데이터 무결성을 확보해준다.
- 개요
    - 웹브라우저, 이메일, 메신저, 인터넷전화와 VoIP 등 네트워크를 통해 정보를 전송하는 경우, 정보를 보내는 측과 받는 측이 통신하여 어떤 암호화 알고리즘을 사용할 것인지를 정하고 공개키 기반의 암호키를 교환한 후에 실제 데이터를 암호화하여 전송하는 방식
    - 공개키와 개인키를 교환하여 보안 세션을 생성하여 통신을 암호화하는 방식을 사용
    - MAC 함수 생성을 위해 다른 암호화 알고리즘을 사용하고, 이전 버전의 보안 소켓 계층(SSL)보다 많은 경고 코드를 포함하고 있다.
- 특징
    - 대부분의 다른 보안 프로토콜은 운영체제 등에 밀접하게 관련되어있지만, 응용 프로그램에서 자체적으로 구현이 가능
    - 응용 계층과 전송 계층 사이에 위치하나, 전송 계층과 더 밀접하게 동작하고, 소켓 지향적인 프로토콜
    - 상대 사이트에 대한 신뢰성을 인증하고, 다양한 암호화 알고리즘을 이용하여 메시지를 암호화
    - 송수신 메시지에 대한 체크섬(checksum) 기능이 있고, 변조를 방지
    - 클라이언트와 서버 두 응용 간에 상대방에 대해 인증을 한다. 메시지 인증 코드 HMAC에 의한 메시지 무결성을 제공한다. 또한, 메시지를 압축한다. 디폴트는 널(Null)로, 무압축이다. 압축 알고리즘은 미리 정해져 있지 않고, 협상으로 지정이 가능하다. 암호화용 세션 키를 생성하기 위한 키를 교환한다. 생성된 공유 비밀키에 의해 암호화된 종단 간의 안전한 연결 통로를 제공한다.[4]
      (추가 내용 작성)
      http://wiki.hash.kr/index.php/TLS




1. SASL
   https://ko.wikipedia.org/wiki/SASL
   https://springboot.cloud/31


###### References
- - https://cho2cee.tistory.com/76
- https://onlywis.tistory.com/14

- https://toptrend.blog/what-is-imei/

- https://www.hardreset.info/ko/articles/what-is-iccid/

- https://xmpp.org/rfcs/rfc3920.html

- https://ko.wikipedia.org/wiki/%EC%A0%84%EC%86%A1_%EA%B3%84%EC%B8%B5_%EB%B3%B4%EC%95%88
- http://wiki.hash.kr/index.php/TLS

- https://ko.wikipedia.org/wiki/SASL
- https://springboot.cloud/31

[맨 위로 이동하기](#){: .btn .btn--primary }{: .align-right} 