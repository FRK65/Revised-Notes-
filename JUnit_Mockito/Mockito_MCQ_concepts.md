
# Mockito MCQ concepts. 

1. what is mockito ?
- Mockito is a framewrok. A mocking framework for unit tests in Java.
- Mockito is a framework that aids in creating and using mock objects in Java unit tests.
---
2. How can you create a mock object using Mockito?
- We can create mock object by "Mockito.mock()"
Example
```java
Account account = Mockito.mock(Account.class);

User user = Mockito.mock(User.class);

Subscription subscription = Mockito.mock(Subscription.class);
```
---
3. Which annotation is used to inject mock objects?
- **"@InjectMocks"** remember Capital I and Mocks plural
Example
```java
@InjectMocks
private VodafoneSystemEventsImpl vodafoneSystemEvents;

@InjectMocks
private ValidateOtpPromptService validateOtpPromptService;

```
---
4. what does @InjectMocks do ? 
- @InjectMocks is a Mockito annotation.
It tells Mockito to create an instance of a class and automatically inject its mocked dependencies into it.
- Works with constructor, setter, or field injection
- Reduces boilerplate (no manual new UserService(mockRepo))
- Used for unit testing only
---
5. What does the verify() method do in Mockito?
- verify() checks behavior, not state.
- verify() is used to check that a method on a mock was called (and how it was called with certain parameters).
Example :

```java
Simple example
@Test
void testSaveCalled() {
    service.saveUser();

    verify(repo).save();
}


verify(repo).save();
verify(repo, times(2)).save();
verify(repo, never()).delete();
verify(repo, atLeastOnce()).save();
verify(repo).save("Alice");
verify(repo).save(anyString());
```
✅ Test passes if repo.save() was called
❌ Test fails if it was not called
1. Verify method was called once (default).
2. Verify number of calls
3. Verify with arguments
4. Verify order
5. What verify() does NOT do
❌ It does not check return values
❌ It does not stub behavior (that’s when())
