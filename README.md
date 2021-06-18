# 로그인/로그아웃/회원가입 구현 - php 
결과값 
 ![image](https://user-images.githubusercontent.com/70025923/122607443-8725ee00-d0b5-11eb-9627-f494fffe622c.png)
 
 php 형식으로 읽기 시작- 읽기 종료
```php
<?php 
?> 
```
php에서 파일을 불러올 때 4가지 형식 
1) include : 다른 php 파일을 불러올 때 사용 
2) include_once : 파일을 불러올때 1번만 로드함 </br>
*에러가 발생하여도 웹 계속 진행  

3) require : 다른 php파일을 불러올 때 사용
4) require_once : 파일을 불러올때 1번만 로드하게 됨 </br> 
**에러 발생시 웹 멈춤!

```php
include "./db.php";
```

post 방식으로 값을 전달할 경우, url에 아무 흔적이 남지 않아 회원가입 or 로그인 기능 구현시 post 사용
 만약, post가 아닌 get 방식을 사용하면 url에 사용자가 입력한 값이 나타나 정보 노출가능 높음
 get & post 방식의 차이 참고 링크 : https://www.codingfactory.net/11603 

```php
 <h1>회원가입</h1>
 <form method="POST" action="regok.php"> 
 
 </form> <h1>로그인</h1>
 <form method="POST" action="logok.php">
```

post 방식으로 전송된 값은 $_post로 받음 
```php
<?php
  if(isset($_SESSION['id'])){
     ?>
     <h2>
       <?php
       echo $_SESSION['name'];
    ?>
  </h2>
```    
위에서 쓰인 isset함수는 변수가 설정되었는지 확인가능하도록 하는 함수
isset($var);의 형태로 쓰임 
즉, $vqr(post method를 적용받는 변수)가 설정되었는지 확인하고, 설정되었으면 true, 설정되지 않았으면 false를 반환 
여기에서는 id가 있으면 name을 echo (화면에 나타내준다) 하고자 함   

isset 예제 

```php
if (isset ($var1)){   
  echo "<p>var1 is set.</p>"; 
  } else "<p>var1 is not set.</p>;
``` 

isset함수와 비슷한 함수 : empty함수 ; 변수가 비어있는지 검사 

문법
```php
empty($var) 
```

다음을 비어있는 것으로 판단 
"" (빈 문자열)
0 (정수 0)
"0" (문자열 0)
NULL
FALSE
array() (빈 배열)
var $var; (클래스 안에서 값 없이 선언된 변수) 

즉, isset() 함수 : 확인하는 변수에 값이 존재& null값이 아니라면 -> true
                  그 외 (변수x or unll) -> false
   empty() : 확인하는 변수의 값이 false, null, 0 -> true

```php
<input type="text" name="name" placeholder="Name" /> <br />
  <input type="text" name="id" placeholder="ID" /> <br />
  <input type="password" name="password" placeholder="Password" /><br />
  <input type="password" name="repassword" placeholder="Re Password" /><br />
  <button type="submit">제출</button><br />
  <a href="select.php"><button type="button">필드 조회하러 가기</button></a> &nbsp;<br />
  ```
  
  input type의 종류 (html) 
1. input type = "text" , input type = "password" 
2. input type = "radio" 
3. input type = "checkbox" 
4. select option 
5. input type ="button" ,input type = "submit", input type = "reset" 
6. input type ="image" 
7. input type ="file"  

예제 
```html
이름 : <input type="text" name="my_name" size="20"
비밀번호 : <input type="password" name="my_password" size="20"> 
```
이름 : <input type="text" name="my_name" size="20"
비밀번호 : <input type="password" name="my_password" size="20"> 

```





