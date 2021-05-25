th:object 를 이용하면 Model 에서 넘겨준 객체를 받아올 수 있다.

th:object 에서 받아온 객체의 필드를 th:field 를 이용해서 참조할 수 있다!

${#fields.hassErrors('필드명')} 를 이용하면 받아온 객체의 해당 필드명에 에러가 있는지 없는지 알 수 있다. ( Controller에서 BindingResult.hasErrors() 랑 비슷한 것 같다...!)

th:errors="*{필드명}" 을 하면 대상 필드와 관련된 에러 메시지로 치환할 수 있다. 

```java
<form role="form" action="/member/signUp" th:object="${signUpForm}" method="post">
        <input type="text" th:filed="*{username}" th:class="${#fields.hasErrors('username')} ? 
            'filedError' : ''" placeholder="아이디를 입력해주세요.">
        <p th:if="${#fields.hasErrors('username')}" th:errors="*{username}">Incorrect data</p>
        <input type="email" id = "email" name = "email" placeholder="이메일을 입력해주세요.">
        <input type="password" id = "password" name = "password" placeholder="비밀번호를 입력해주세요.">
        <input type="submit" value="Sign Up">
    </form>
```

