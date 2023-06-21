# OAuth Login Spring Boot Project

스프링부트 환경 OAuth 로그인 예제 프로젝트입니다.
본 프로젝트에서는 구글, 네이버, 카카오 네 개의 OAuth 서비스 제공자에 대한 설정을 소개합니다.

# 스프링부트 로그인

- 앱, 웹 서비스에서 로그인 구현은 세션, 쿠키 등의 역할 및 보안에도 신경을 써야함.
- 이러한 구현을 단축시키는것을 스프링부트에서 `Spring Security` 및 `OAuth2`를 포함한 다양한 프레임 워크와 라이브러리를 이용하여 REST API 기반의 기능 구현 방법에 대한 정리.

# 스프링부트 소셜 로그인

- 스프링부트에서 구글, 페이스북, 네이버, 카카오 등 다양한 서비스를 이용하여 소셜 로그인 구현이 가능함.
- OAuth 로그인 구현을 위해서는 스프링 시큐리티, 스프링 시큐리티 OAuth2 클라이언트를 사용함.

# Spring Security

- `Spring Security`는 Spring 기반의 어플리케이션 권한과 인증, 인가 등의 보안을 담당하는 하위 프레임워크.
- 스프링 시큐리티는 **인증**과 **권한**을 Filter 흐름에 따라 처리하게 구현됨.

- OAuth2란?
    - Open Authentication2의 약자로 인증 및 권한획득을 위한 업계표준 프로토콜.
    - 보안수준이 어느정도 검증된 플랫폼의 API를 이용하여 사용자 인증과 리소스에 대한 권한 획득(인가)를 할 수 있도록 해주는 역할을 하고, 대부분의 영향력 있고 OAuth2 인증을 제공하는 플랫폼들은 모두 OAuth2 규칙을 지키는 API를 제공함.

- OAuth2 프로토콜 탄생배경
    - 보안수준이 검증되지 않은 플랫폼에 동일한 아이디와 패스워드를 사용하는 상황이 빈번히 발생
    - 많은 플랫폼에 회원 가입시 동일 아이디, 패스워드를 사용하는 경우가 많아 보안에 취약해짐.
    - OAuth 인증을 통하면 신뢰할 수 있는 플랫폼이 인증과 리소스에 대한 권한을 외부 플랫폼에 부여하므로 보안의 문제 해결 및 UX적으로도 편리한 장점이 있음.

- Oauth2 구성요소
    1.  Resource Owner: 사용자
    2. Client: 리소스 서버에서 제공해주는 자원을 사용하는 외부 플랫폼
    3. Authorization Server: 외부 플랫폼이 리소스 서버의 사용자 자원을 사용하기 위한 인증 서버
    4. Resource Server: 사용자의 자원을 제공해주는 서버
    - 위의 구성은 예를들어, 카카오 계정을 통해 카카오 로그인 기능을 지원하는 외부 플랫폼에 로그인을 할때 외부 플랫폼을 통하여 카카오 인증 서버(Authorization Server)에 인증 요청을 하게 되고 외부 플랫폼은 카카오의 정보들을 사용할 수 있는 권한을 가짐.

- OAuth2 인증 종류
    1. Authorization Code Grant: 권한 코드 승인 방식
        - Server Side에서 인증 처리시 이용하는 방식으로 Resource Owner로부터 리소스 사용에 대한 허락을 의미하는 Autorization Code를 이용하여 Access Token을 요청하는 방식.
        - 이 방식은 AT가 바로 클라이언트에 전달되지 않기에 보안에 좋은 특징이 있음.
    2. Implicit Grant: 암시적 승인 방식
        - 권한 코드 없이 바로 토큰을 발급해 사용하는 방식으로 브라우저, 앱과 같은 서버의 연동이 없는 어플리케이션에서 주로 사용됨.
        - 권한 코드 검증이 들어가지 않기에 보통 Read Only 서비스에서 사용하는 것이 좋음.
    3. Password Credentials Grant: 비밀번호 자격 증명 방식
        - Client에 Service Provider(구글, 카카오 등…)의 아이디와 패스워드를 저장해두고 사용하는 방식.
        - Client에 Service Provider의 관계가 긴밀할 경우 사용하는 것이 좋음.
    4. Client Credentials Grant: 클라이언트 자격 증명 방식
        - Client와 Resource Owner가 같을 경우 사용하는 인증 방식.
        - 2개가 같기에 추가 인증은 필요없고 Authorization Server로부터 토큰을 받을 수 있음.

- Spring OAuth2 Client
    - OAuth 인증을 위해서는 인증을 위한 다양한 절차대로 진행해야 인증이 가능.
    - 이러한 절차들을 설정 한번으로 간단히 해주는것이 `Spring OAuth2 Client`

## 블로그 바로가기

[\[Spring Boot\] OAuth2 소셜(구글, 페이스북, 네이버, 카카오) 로그인 완벽 가이드](https://deeplify.dev/back-end/spring/oauth2-social-login)

## 노션
[개인노션 정리](https://versed-parakeet-e80.notion.site/SpringBoot-OAuth2-Example-6fd7c7bfd616416a8f3fafe27ce5d955?pvs=25)
## 기본 설정

1. 이 프로젝트는 데이터베이스와 연결되어야합니다. (실행하시려면 dbname: oauth_login_tutorial을 만들어주세요.)
2. 하단 application.yml 파일에 각 서비스 제공자 별 `client-id`와 `client-secret` 두 가지를 각각 등록해 주셔야합니다.

# spring-oauth-sample
