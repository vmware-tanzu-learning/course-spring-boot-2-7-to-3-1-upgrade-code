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

## Remove hard-coded Spring/Spring Boot Dependencies

- remove hardcoded `spring-data-jdbc` version
- Code Compiles, No Errors or Warnings

## Update Non Spring/Spring Boot Managed Dependencies

- remove hardcoded `lombok` version
- Code Compiles, No Errors or Warnings
- moved hardcoded `itextpdf` version to <properties>

### Upgrade Spring Security Version

- Remove Spring Security version override and upgrade Spring Security to `6.1.3`
- Spring Security deprecations
  ```
  [WARNING] ... src/main/java/example/cashcard/SecurityConfig.java:[24,13] authorizeHttpRequests() in org.springframework.security.config.annotation.web.builders.HttpSecurity has been deprecated and marked for removal
  [WARNING] ... src/main/java/example/cashcard/SecurityConfig.java:[27,17] and() in org.springframework.security.config.annotation.web.configurers.AuthorizeHttpRequestsConfigurer.AuthorizationManagerRequestMatcherRegistry has been deprecated and marked for removal
  [WARNING] ... src/main/java/example/cashcard/SecurityConfig.java:[28,17] csrf() in org.springframework.security.config.annotation.web.builders.HttpSecurity has been deprecated and marked for removal
  ```
  - [Migrating to Spring Security 6](https://docs.spring.io/spring-security/reference/6.0/migration/index.html)
- Update `http.authorizeHttpRequests` to use the new customizer interface
- Update `csrf` to use the new customizer interface

_Result:_ code compiles without errors or warnings

## Test - Initial Test Execution

_Result:_ code compiles without errors or warnings and all tests pass

## Test Dependency Housekeeping

- ~~Remove explicit version of `aspectj-core`~~
- Remove explicit `aspectj-core` dependency
  - It's managed by `spring-boot-starter-test`

_Result:_ code compiles without errors or warnings and all tests pass

## Address deprecated Spring Properties

- Property `spring.kafka.streams.cache-max-size-buffering` is deprecated
  - replaced by `spring.kafka.streams.state-store-cache-max-size`