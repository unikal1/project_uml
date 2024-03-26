# 한바구니 UML 및 클래스 구성

## 패키지 및 클래스 구성
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
