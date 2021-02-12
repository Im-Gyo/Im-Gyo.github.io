---
layout : post
title : Spring RestTemplate 정리
category : Spring
---
# Spring RestTemplate 정리 및 기록
## 포스팅 이유
SpringBoot 게시판 작성 중에 ControllerTest코드 작성을 하다가
`ResponseEntity<Long> responseEntity = restTemplate.postForEntity(url, requestDto, Long.class);`  
이 코드가 생소해 자세히 분석하기 위해서 포스팅을 하려고 한다.

일단 스프링 프레임워크에서 동기방식의 RestTemplate클래스가 있다.
- RestTemplate
Spring 3부터 지원 됐고 REST API 호출 이후 응답을 받을 때 까지 기다리는 동기방식이다.

##### 메서드 정리
![](https://github.com/Im-Gyo/Im-Gyo.github.io/blob/master/_screenshots/ResponseEntity2.PNG?raw=true)  
※ 출처 : [https://advenoh.tistory.com/46](https://advenoh.tistory.com/46) (advenoh님 블로그)  

이 중에서 코드에 사용된 postForEntity() 메서드에 대해서 알아보고자 한다.
해당 메서드를 따라가보니
![](https://github.com/Im-Gyo/Im-Gyo.github.io/blob/master/_screenshots/ResponseEntity1.PNG?raw=true)
밑줄과 같이 인자값에 대한 정보들이 있다.

Spring API문서를 찾아본 결과
[https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/web/client/RestTemplate.html](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/web/client/RestTemplate.html)


**지정된 개체를 URL에 게시해서 새 리소스를 생성하고 응답을 응답 엔티티로 반환한다는 뜻이다.**


