---
title:  "[Vocabulary] 개인 공부 중 모르는 영어 단어 2"

categories:
- Vocabulary
tags:
- [Programming, Vocabulary]

toc: true
toc_sticky: true

date: 2022-12-27
last_modified_at: 2022-12-28
---

1. FQDN (Fully Qualified Domain Name)

- 전체 도메인 네임
- 도메인 전체 이름을 표기하는 방식을 의미 | 호스트와 도메인을 함께 명시하여 전체 경로를 모두 표기하는 것
- 전체 주소 도메인 네임의 레이블의 계층

![en wikipedia org](https://user-images.githubusercontent.com/61777583/209635776-1f8d21d8-7a4c-459e-ae54-1029b0621acc.png)

- 예제
    - www.naver.com
        - www -> host
        - naver.com -> domain

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

###### References

- https://cho2cee.tistory.com/76
- https://onlywis.tistory.com/14
- https://toptrend.blog/what-is-imei/
- https://www.hardreset.info/ko/articles/what-is-iccid/
- https://xmpp.org/rfcs/rfc3920.html

[맨 위로 이동하기](#){: .btn .btn--primary }{: .align-right} 