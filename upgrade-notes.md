# 3.1 Upgrade Notes

## Initial baseline

- Code compiled successfully
  - errors
  - Deprecation warnings
    -  src/main/java/example/cashcard/SecurityConfig.java uses or overrides a deprecated API.
- found disabled/broken test - CashCardApplicationTests#shouldReturnACashCardWhenDataIsSaved
    - fixed broken test and re-enabled

_Result:_ code compiles without errors or warnings and all tests pass

