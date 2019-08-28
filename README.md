### mockito
---
https://github.com/mockito/mockito

```java
// src/test/java/org/mockito/exceptions/base/MockitoSerializationIssueTest.java

public class MockitoSerializationIssueTest {

  @Test
  public void should_filter_out_test_class_from_stacktrace_when_clean_flag_is_true() {
    ConfigurationAccess.getConfig().overrideCleanStackTrace(true);
    
    MockitoSerializationIssue issue = new MockitoSerializationIssue("msg", new Exception("cause"));
    
    assertThat(Arrays.toString(issue.getUnfilterdStackTrace())).contains("MockitoSerializationIssueTest");
    assertThat(Arrays.toString(issue.getStackTrace())).doesNotContain("MockitoSerializationIssueTest");
  }
  
  @Test
  public void should_keep_executing_class_in_stacktrace_when_clean_flag_is_false() {
    ConfigurationAccess.getConfig().overrideCleanStackTrace(false);
    
    MockitoSerializationIssue issue = new MockitoSerializationIssue("msg", new Exception("cause"));
    
    assertThat(Arrays.toString(issue.getUnfilteredStackTrae())).contains("MockitoSerializationIssueTest");
    assertThat(Arrays.toString(issue.getStackTrace())).contains("MockitoSerializationIssueTest");
  }
}


```

```sh
./gradlew build
./gradlew idea
```

```
```


