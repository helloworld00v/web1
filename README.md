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
 ![image](https://user-images.githubusercontent.com/70025923/122631752-d9442f00-d108-11eb-9d29-0ba57c40b190.png)

 
 get & post 방식의 차이 참고 링크 : https://www.codingfactory.net/11603 

```php
 <h1>회원가입</h1>
 <form method="POST" action="regok.php"> 
 
 </form> <h1>로그인</h1>
 <form method="POST" action="logok.php"> 
``` 
html - <form> 태그
 > 폼 태그 동작방법 
 1. 폼이 있는 웹 페이지 방문
 2. 폼 내용 입력 
 3. 폼 안의 모든 데이터를 서버로 보냄 
 4. 서버는 받은 폼 데이터를 처리위해 웹 프로그램으로 넘김 
 5. 웹 프로그램은 폼 데이터 처리 
 6. 처리결과에 따른 새로운 html 페이지를 웹 서버에 보냄 
 7. 웹 서버는 받은 html페이지를 브라우저에 보냄 
 8. 브라우저는 받은 html페이지를 보여줌 
 ![image](https://user-images.githubusercontent.com/70025923/122631661-283d9480-d108-11eb-93fb-a53a2879e875.png) 
 
 > 폼 태그 속성 
 - action : 폼을 전송할 서버 쪽 스크립트 파일 지정   
 - name : 폼을 식별하기 위한 이름 지정 
 - accept-charset : 폼 전송에 사용할 문자 인코딩 지정 
 - target : action에서 지정한 스크립트 파일을 현재 창이 아닌 다른 위치에서 열도록 지정 
 - method : 폼을 서버에 전송할 http 메소드를 지정 (get 또는 post) 
 
 예제 
 ```html
 <html>
  <head>
  </head>
  
  <body>
   <form action = "http://localhost:8080/form.jsp" accept-charset="uft-8"
         name="person_info" method="get"> 
   </form>
  </body>
  <html> 
   ```
> 폼을 구성하는 다양한 elements
   <fieldset> 태그 
    - 폼 태그 안에 관련 있는 폼 엘리먼트들을 그룹화할 떄 사용 
   <legend> 태그     
    - <fieldset>태그 하위에 <legend>태그를 사용하여 그룹화한 폼 엘리먼트들을 목적에 맞게 이름 지정 
    https://www.nextree.co.kr/content/images/2021/01/hjkwon-140328-form_-04.png  
    
    위의 그림 코드 
    ```html
    <head>
    </head>
    
    <body> 
     <form action = "#" accept-charset= "uft-8" name="person_info" method = get">
         <fieldset style = "width:150"> 
             <legend>개인 정보 입력 </legend>
                  이름 : <input type = "text" name="name"/><br><br>
                  나이 : <input type = "test" name="age"/><br><br> 
         </fieldset>
        <br>
        <fieldset style = "width:180; height:180">
           <legend>여가 활동 </legend>
                취미 : <input type = "text" name = "hobby"/> <br><br> 
                특기 : <input type = "text" name = "specialty"/> <br><br> 
            </fieldset>                                                     
           </form>                                            
         </body>                  
   </html> 
                                                            ```
   추가적인 input 태그 참고 링크 : https://www.nextree.co.kr/p8428/  

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
```php
<input type="text" name="name" placeholder="Name" /> <br />
  <input type="text" name="id" placeholder="ID" /> <br />
  <input type="password" name="password" placeholder="Password" /><br />
  <input type="password" name="repassword" placeholder="Re Password" /><br />
  <button type="submit">제출</button><br />
  <a href="select.php"><button type="button">필드 조회하러 가기</button></a> &nbsp;<br />
  ```
  
  placeholder - 짧은 힌트 ( input값에 무엇을 넣어야하는지에 대한 ) 
  syntax 
  ```html    
<input placeholder="text">    
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
.. 기타 예제는 https://coding-factory.tistory.com/24 참고    

이처럼 <input>태그는 사용자가 다양하게 폼 태그에 입력할 수 있는 공간을 만들어줌 


 
   

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
    
    
    <h2> db.php <h2> 
```php 
     session_start();
``` 
php에서 sessiont이란 여러 페이지가 존재할 떄, 여러 페이지에 걸쳐서 변수정보를 저장하는 방식이다. 
쿠키와 달리 정보는 user computer에 저장되지 않는다.  
세션은 session_start() 함수로 시작한다. 
세션 변수는 php global variable 인 $_SESSION으로 받는다. 

코드예제 
```php
     <?php
session_start();
?>
<!DOCTYPE html>
<html>
<body>

<?php
$_SESSION[ 'no' ] = 123;
$_SESSION[ 'username' ] = 'abc'
\\ 세션의 no에 123을, username에 abc를 저장    
echo $_SESSION['no']; 
\\세션의 no 값을 출력 
echo $_SESSION['username']; 
\\세션의 username값 출력 

var_dump($_SESSION); 
\\세션의 모든 값 출력 & 변수의 정보 출력 
?>

</body>
</html> 
     ```  
전체 코드 
     
```php 
     <!doctype html>
<html lang="ko">
  <head>
    <meta charset="utf-8">
    <title>PHP</title>
    <style>
      body { 
        font-family: Consolas, monospace;
      }
    </style>
  </head>
  <body>
    <h1>Session</h1>
    <?php
      session_start();
      $_SESSION[ 'no' ] = 123;
      $_SESSION[ 'username' ] = 'abc';
      echo session_id();
      echo '<br>';
      echo $_SESSION[ 'no' ];
      echo '<br>';
      echo $_SESSION[ 'username' ];
      echo '<br>';
      var_dump( $_SESSION );
    ?>
  </body>
</html>
 ``` 
     
결과값 
     ![image](https://user-images.githubusercontent.com/70025923/122632268-b0be3400-d10c-11eb-90fb-5213ffb63795.png)

array(2) { ["no"]=> int(123) ["username"]=> string(3) "abc" } 
<br> 
    의미 : 2개의 값을 가진 배열이고, no값은 정수 123, username값은 3개의 문자로 이루어진 문자열이고 값은 abc입니다. 
     
추가 : php session 삭제 
```php
     <?php
session_start();
?>
<!DOCTYPE html>
<html>
<body>

<?php
// remove all session variables
session_unset();

// destroy the session
session_destroy();
?>

</body>
</html>
```
 결과값 : All session variables are now removed, and the session is destroyed. 
     
     
 ```php
     $conn = mysqli_connect("localhost", "root","001012", "php");
$conn->set_charset("utf8"); 
 ```
      
mysqli_connet : php에서 mySQL을 연결해주는 함수 
mysqli_close : mysqli_connet함수를 통해 연결한 객체의 연결을 해제 
     
     syntax
     
 ```php
     mysqli_connect([아이피], [아이디], [비밀번호], [DB명], [포트]);
\\포트의 경우, 기본포트인 경우 입력하지 않고 사용하여도 무관 
\\ [참고] MySQL의 기본 포트 : 3306
     mysqli_close([연결 객체]);

``` 
     예제 
     
```PHP 
       $conn = mysqli_connect("127.0.0.1", "root", "1234", "test_db");
       print_r($conn);  \\$conn 변수 확인 (결과값 : mysqli Object ( ))
       mysqli_close($conn);  
```
       
     
