# Chapter41 - 소스 파일 여러 개로 분리하기

<details><summary>주요 내용 
</summary>

## 소스 파일 여러 개로 분리하기
  
 - math.kt
  
 ```kotlin
  
fun max(a : Int, b:Int) : Int = 
    if (a>b) a else b 
fun min(a : Int, b:Int) : Int = 
    if (a<b) a else b 

fun abs(num : Int) : Int = 
    if (num>=0) num else - num
  
 ```
  
 - main.kt
  
 ```kotlin
  
 fun main(){
    val a = 20
    val b = - 30

    println(max(a,abs(b))) //같은 패키지 내에 존재하면 함수를 그대로 가져다 쓴다 
} 
  
  
 ``` 
  
  

</details>

---


# Chapter42 - 패키지(Package)
<details><summary>주요 내용
</summary>

## 패키지(Package)
 
- 서로 관련 있는 소스 파일들 하나의 폴더로 관리한다  
- 가급적이면 소문자로 짓는다
 
- 만약, 소스 파일이 여러 겹의 폴더 속에 있다면

` package 폴더명1.폴더명2.폴더명3`
  
  
  
</details>


---


# Chapter43 - 다른 패키지의 함수 호출하기
<details><summary>주요 내용
</summary>

  ## 다른 패키지의 함수 호출하기 

- `패키지 이름.함수 이름()` 으로 호출한다
  
  
  
</details>


---



# Chapter44 - import
<details><summary>주요 내용
</summary>

 ## import 
  
- **import 키워드** 를 사용하면 다른 패키지에 선언된 함수를 패키지 이름 없이 호출할 수 있다

- 해당 함수를 패키지 이름 없이 호출할 때 

`import 패키지 이름.함수 이름`
  
- 해당 패키지에 들어있는 모든 함수를 패키지 이름 없이 호출할 때 

`import 패키지 이름.*`
  

- 새로운 이름으로 해당 함수를 호출할 때

`import 패키지 이름.함수 이름 as 새로운 이름`
  
  
</details>



---




# Chapter45 - 객체(Object)
<details><summary>주요 내용
</summary>

## 객체 
- 서로 연관 있는 변수(속성)들을 묶어놓은 데이터 덩어리
- **프로퍼티(Property)** : 객체에 포함된 변수들. 속성. 프로퍼티는 반드시 선언과 동시에 초기화해야 한다 
- object에서 맨 앞은 소문자이다
  
  
```kotlin
  
  fun main(){
    val person = object{ 
        val name: String = "홍길동"
        val age : Int = 36
    }
}
  
```  
  
  
</details>



---





# Chapter46 - 메모리의 힙(Heap) 영역
<details><summary>주요 내용
</summary>

## 메모리의 힙(Heap) 영역

- 객체 생성 시 object {...} 부분이 실행될 때 힙 영역에 객체가 생성된다. 
- Stack과 달리 임의의 위치에 객체가 생성된다 
- object 선언 시 object 이름을 저장한 Stack에는 **실제 값을 가지지 않고 객체의 좌표만 저장하는 참조 변수(Reference Variable)** 이 저장된다  
  
</details>



---




# Chapter47 - 클래스(Class)
<details><summary>주요 내용
</summary>

## 클래스(Class)

```kotlin
  
  class 클래스 이름
  {
    프로퍼티
  }
  
```  
  
 ```kotlin
  
  class Person
{
    var name : String = ""
    var age : Int = 0

}

fun main(){
    var kim : Person = Person()
    kim.name = "김유신"
    kim.age = 50
    println(kim.name)
    println(kim.age)
}
  
 ``` 
  
  
- 클래스 이름이 파일 이름과 같아야 할 의무가 없으며, 한 파일 내에 여러 개의 public 클래스를 선언할 수도 있다 
  
- object 키워드로 객체를 일일이 생성했을 때는 객체의 타입에 이름도 없었고 객체의 형태가 완전히 같아도 서로 다른 타입으로 인식된다. 그러나 클래스로 생성된 객체는 모두 동일한 타입을 갖는다  
  
- **인스턴스(Instance)** : 클래스로부터 생성된 객체
  
- 코틀린의 기본 접근지정자는 default인 자바와는 달리 public이다. 
  
  
  
</details>



---




# Chapter48
<details><summary>주요 내용
</summary>



  
  
  
</details>





---





# Chapter49
<details><summary>주요 내용
</summary>



  
  
  
</details>


---




# Chapter50
<details><summary>주요 내용
</summary>



  
  
  
</details>


---




# Chapter51
<details><summary>주요 내용
</summary>



  
  
  
</details>

---


# Chapter52
<details><summary>주요 내용
</summary>



  
  
  
</details>

---


# Chapter53
<details><summary>주요 내용
</summary>



  
  
  
</details>

---


# Chapter54
<details><summary>주요 내용
</summary>



  
  
  
</details>




---


# Chapter55
<details><summary>주요 내용
</summary>



  
  
  
</details>





---


# Chapter56
<details><summary>주요 내용
</summary>



  
  
  
</details>





---


# Chapter57
<details><summary>주요 내용
</summary>



  
  
  
</details>





---


# Chapter58
<details><summary>주요 내용
</summary>



  
  
  
</details>



---


# Chapter59
<details><summary>주요 내용
</summary>



  
  
  
</details>



---


# Chapter60
<details><summary>주요 내용
</summary>



  
  
  
</details>


