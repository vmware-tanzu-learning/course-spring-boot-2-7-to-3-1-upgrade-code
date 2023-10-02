# 3.1 Upgrade Notes

## Initial baseline

- Code compiled successfully
  - errors
  - Deprecation warnings
    -  src/main/java/example/cashcard/SecurityConfig.java uses or overrides a deprecated API.
- found disabled/broken test - CashCardApplicationTests#shouldReturnACashCardWhenDataIsSaved
    - fixed broken test and re-enabled

_Result:_ code compiles without errors or warnings and all tests pass

## Major Release Considerations

- Upgrade Spring Security to `5.8.5`
- Spring Security deprecations
  - [INFO] /course-spring-boot-2-7-to-3-1-upgrade-code/src/main/java/example/cashcard/SecurityConfig.java: /course-spring-boot-2-7-to-3-1-upgrade-code/src/main/java/example/cashcard/SecurityConfig.java uses or overrides a deprecated API.
  - [INFO] /course-spring-boot-2-7-to-3-1-upgrade-code/src/main/java/example/cashcard/SecurityConfig.java
  - Reference: https://docs.spring.io/spring-security/reference/5.8/migration/index.html
- Replace `WebSecurityConfigurerAdapter` super class with `SecurityFilterChain` bean definition
- Replace `antMatcher` with `requestMatcher` builder method
- Replace `new Pbkdf2PasswordEncoder` with static factory method for Spring Security 5.8
- Add `@Configuration` annotation, which is removed in Spring Security 6.0

_Result:_ code compiles without errors or warnings and all tests pass (no skipped tests)!

## Upgrade Spring Boot Parent Version

- Code Compiles, No Errors or Warnings
