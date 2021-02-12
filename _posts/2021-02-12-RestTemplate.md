---
layout : post
title : Spring RestTemplate 정리
category : Spring
---
# Spring RestTemplate 정리 및 기록
## 포스팅 이유
SpringBoot 게시판 작성 중에 ControllerTest코드 작성을 하다가
``` ResponseEntity<Long> responseEntity = restTemplate.postForEntity(url, requestDto, Long.class);```
이 코드가 생소해 자세히 분석하기 위해서 포스팅을 하려고 한다.

일단 스프링 프레임워크에서 동기방식의 RestTemplate클래스가 있다.
- RestTemplate
Spring 3부터 지원 됐고 REST API 호출 이후 응답을 받을 때 까지 기다리는 동기방식이다.

##### 메서드 정리
| 메서드 | HTTP | 설명 |
|--------|--------|--------|
|getForObject|GET|주어진 URL 주소로 HTTP GET 메서드로 객체로 결과를 반환받는다|
|getForEntity|GET|주어진 URL 주소로 HTTP GET 메서드로 결과는 ResponseEntity로 반환받는다|
|postForLocation|POST|POST 요청을 보내고 결과로 헤더에 저장된 URI를 결과로 반환받는다|
|postForObject|POST|POST 요청을 보내고 객체로 결과를 반환받는다|
|postForEntity|POST|POST 요청을 보내고 결과로 ResponseEntity로 반환받는다|
|delete|DELETE|주어진 URL 주소로 HTTP DELETE 메서드를 실행한다|
|headForHeaders|HEADER|헤더의 모든 정보를 얻을 수 있으면 HTTP HEAD 메서드를 사용한다|
|put|PUT|주어진 URL 주소로 HTTP PUT 메서드를 실행한다|
|patchForObject|PATCH|주어진 URL 주소로 HTTP PATCH 메서드를 실행한다|
|optionsForAllow|OPTIONS|주어진 URL 주소에서 지원하는 HTTP 메서드를 조회한다|
|exchange|any|HTTP 헤더를 새로 만들 수 있고 어떤 HTTP 메서드도 사용가능하다|
|execute|any|Request/Response 콜백을 수정할 수 있다|

이 중에서 코드에 사용된 postForEntity() 메서드에 대해서 알아보고자 한다.
해당 메서드를 따라가보니
![](https://github.com/Im-Gyo/Im-Gyo.github.io/blob/master/_screenshots/ResponseEntity1.PNG?raw=true)
밑줄과 같이 인자값에 대한 정보들이 있다.

Spring API문서를 찾아본 결과
[https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/web/client/RestTemplate.html](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/web/client/RestTemplate.html)


**지정된 개체를 URL에 게시해서 새 리소스를 생성하고 응답을 응답 엔티티로 반환한다는 뜻이다.**


