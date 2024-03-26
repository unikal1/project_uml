# 한바구니 UML 및 클래스 구성

## 패키지 및 클래스 구성
<details>
  <summary>패키지 구조 열기</summary>
 
  ```
  📦project
   ┣ 📂domain
   ┃ ┣ 📂university
   ┃ ┃ ┣ 📂dao
   ┃ ┃ ┃ ┣ 📜DormitoryRepository.java
   ┃ ┃ ┃ ┗ 📜UniversityRepository.java
   ┃ ┃ ┣ 📂domain
   ┃ ┃ ┃ ┣ 📜Dormitory.java
   ┃ ┃ ┃ ┗ 📜University.java
   ┃ ┃ ┣ 📂dto
   ┃ ┃ ┃ ┗ 📜UniversityDto.java
   ┃ ┃ ┣ 📂service
   ┃ ┃ ┃ ┣ 📜UniversityService.java
   ┃ ┃ ┃ ┗ 📜UniversityServiceImpl.java
   ┃ ┃ ┗ 📜UniversityCode.java
   ┃ ┗ 📂user
   ┃ ┃ ┣ 📂api
   ┃ ┃ ┃ ┣ 📜RegisterController.java
   ┃ ┃ ┃ ┗ 📜SignInController.java
   ┃ ┃ ┣ 📂dao
   ┃ ┃ ┃ ┗ 📜MemberRepository.java
   ┃ ┃ ┣ 📂domain
   ┃ ┃ ┃ ┣ 📜Member.java
   ┃ ┃ ┃ ┗ 📜Profile.java
   ┃ ┃ ┣ 📂dto
   ┃ ┃ ┃ ┣ 📜RegisterDto.java
   ┃ ┃ ┃ ┗ 📜SignInDto.java
   ┃ ┃ ┗ 📂service
   ┃ ┃ ┃ ┣ 📜MemberService.java
   ┃ ┃ ┃ ┣ 📜MemberServiceImpl.java
   ┃ ┃ ┃ ┣ 📜MemberSignInService.java
   ┃ ┃ ┃ ┗ 📜MemberSignInServiceImpl.java
   ┣ 📂global
   ┃ ┣ 📂auth
   ┃ ┃ ┣ 📂jwtTokenManage
   ┃ ┃ ┃ ┣ 📂dao
   ┃ ┃ ┃ ┃ ┗ 📜RefreshTokenRepository.java
   ┃ ┃ ┃ ┣ 📂domain
   ┃ ┃ ┃ ┃ ┣ 📜JwtToken.java
   ┃ ┃ ┃ ┃ ┗ 📜RefreshToken.java
   ┃ ┃ ┃ ┣ 📂dto
   ┃ ┃ ┃ ┃ ┗ 📜RefreshTokenDto.java
   ┃ ┃ ┃ ┣ 📂exception
   ┃ ┃ ┃ ┃ ┗ 📜RefreshTokenNotFoundException.java
   ┃ ┃ ┃ ┣ 📂filter
   ┃ ┃ ┃ ┃ ┗ 📜JwtAuthenticationFilter.java
   ┃ ┃ ┃ ┣ 📂service
   ┃ ┃ ┃ ┃ ┣ 📜CustomUserDetailsService.java
   ┃ ┃ ┃ ┃ ┣ 📜JwtTokenProvider.java
   ┃ ┃ ┃ ┃ ┗ 📜TokenRefresh.java
   ┃ ┃ ┃ ┗ 📂utils
   ┃ ┃ ┣ 📂oAuthManage
   ┃ ┃ ┗ 📜Roles.java
   ┃ ┣ 📂config
   ┃ ┃ ┗ 📜SecurityConfig.java
   ┃ ┣ 📂infra
   ┃ ┗ 📂utils
   ┃ ┃ ┗ 📜SecurityUtils.java
   ┗ 📜ProjectApplication.java 
  
  ```
</details>

# 회원가입 로직

이는 `domain` -> `user` 패키지에 속한  
`Member`, `MemberService`, `MemberServiceImpl`, `RegisterController`를 사용하여 기본 정보 저장 로직을 구현하고  
`Profile`, `ProfileService`, 'ProfileServiceImpl`, `ProfileController`를 사용하여 회원의 세부 정보 로직을 구현한다.( 미구현 )  

## API
- URI pattern    : `/register`  
- controller by  : `RegisterController`  
- data Type      : `JSON - RestAPI` 
- DTO is         : `RegisterDto`

| name           | type     | notEmpty | size  | etc  |
|----------------|----------|----------|-------|------|
| username       | `String` | true     | 4~20  | NULL |
| password       | `String` | true     | 4~60  | NULL |
| memberNickname | `String` | true     | 2~10  | NULL |
| memberName     | `String` | true     | 2~10  | NULL |

## Member Entity

| name           | type           | nullable | etc               |
|----------------|----------------|----------|-------------------|
| id             | `Long`         | false    |                   |
| profile        | `String`       | false    |                   |
| username       | `String`       | false    |                   |
| password       | `String`       | false    |                   |
| memberName     | `String`       | false    |                   |
| memberNickname | `String`       | false    |                   |
| roles          | `List<String>` |          | default : "GUEST" |

Spring security의 `UserDetails`를 상속받았다. 이후 `UsernamePasswordAuthenticationToken`이 호출되면  
해당 엔티티에서 아이디와 비밀번호를 조회한다.

### getAuthorities
- return
    - Collection<? extends GrantedAuthority>
    - 권한 정보 문자열이 저장된 권한 객체 `GrantedAuthority` 타입의 컬렉션

엔티티에 저장되어 있는 문자열 리스트 `roles`를 객체로 변환하여 반환.  
`builder`에 의한 객체 생성 및 non-parameter constructor가 `protected`로 설정됨.  

