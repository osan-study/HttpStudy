# Chapter 21. 로깅과 사용 추적

# 1. 로그(log)란?

로깅을 하는 이유는 기본적으로 서버나 프록시의 문제를 찾거나, 웹 사이트 접근 통계를 내려고 로깅을 한다. 보통은 트랜잭션의 기본적인 항목들만 로깅한다.

- HTTP 메서드
- 클라이언트와 서버의 HTTP 버전
- 요청받은 리소스의 URL
- 응답의 HTTP 상태 코드
- 요청과 응답 메시지의 크기
- 트랜잭션이 일어난 시간
- Referer와 User-Agent 헤더 값

# 2. 로그 포맷

- 상용 혹은 오픈 소스 HTTP 애플리케이션은 대부분, 표준 로그 포맷을 한 개 이상 지원한다.
- 애플리케이션이 더 많은 표준 포맷을 지원하고 관리자가 사용할 수록 얻을 수 있는 이점이 많다.

## 2.1 일반 로그 포맷

가장 일반적인 포맷이며, 많은 서버들이 기본으로 사용한다.

| 필드 | 설명 |
| --- | --- |
| remotehost | 요청한 컴퓨터의 호스트 명 혹은 IP주소 |
| username | ident 검색을 수행했다면, 인증된 요청자의 사용자 이름 |
| auth-username | 인증을 수행했다면, 인증된 요청자의 이름 |
| teimstamp | 요청 날짜와 시간 |
| request-line | HTTP 요청의 행을 그대로 기술 |
| response-code | 응답으로 보내는 HTTP 상태 코드 |
| response-size | 응답 엔터티의 Content-Length, 아무런 엔터티를 반환하지 않으면 값이 0이 된다. |

## 2.2 혼합 로그 포맷

이 포맷은 아파치 같은 서버들이 지원한다. 추가된 필드 두 개를 제외하면 일반 로그 포맷과 같다.

| 필드 | 설명 |
| --- | --- |
| Referer | Referer HTTP 헤더의 값(해당 URL을 요청자가 어디서 찾았는지에 관한 정보) |
| User-Agent | User-Agent Referer HTTP 헤더의 값(요청을 만든 HTTP 클라이언트 애플리케이션) |