# Chapter1

<details><summary>주요 내용
</summary>

  ## Hello, World!
  
- 클래스에서 완전히 독립된 함수를 가질 수 있으며 이를 **패키지 레벨 함수**라고 한다
- 타입을 맨 끝에 적는다 
  
```kotlin
  fun main(){
    println("Hello World!")
  }
  
  fun add(a : Int, b : Int) : Int {
    return a+b
  }
```

</details>

---


# Chapter2
<details><summary>주요 내용
</summary>

## 표현식(Expression)
 - 하나의 값으로 수렴하는 수식 뭉치를 **표현식**이라고 한다
 - 코틀린에서는 표현식이 단독으로 오는 것을 허용한다
  
```kotlin 
  fun main(args: Array<String>) : Unit{
    53 + 62 - 126
  }
  
  fun main(args: Array<String>) : Unit{
    println(53 +
          62
          -126) 
  //가능하다
  }
  
  
```
  
  
  
</details>


---


# Chapter3
<details><summary>주요 내용
</summary>

## 변수(Variable)
  
```kotlin
fun main(args:Array<String>) : Unit {
    var total : Int
    total = 0

    val a : Int = 10 + 53 - 7
    println(a)

    val b : Int = 43 + 75 + a
    println(b)

    total = a + b
    println(total)
}
  
  
```

- 식별자 규칙 

 |형태|이름|
 |---|---|
 |anyVariableName | 낙타 표기법(Camel Case) | 
 |AnyVariableName| 파스칼 표기법(Pascal Case) |
 |any_variable_name| 뱀 표기법(Snake Case) | 
 
- 코틀린은 **Camel Case를 주로 사용**한다 
 
- 코틀린은 자바와 달리 원시(Primitive) 타입이 없다. 즉, 코틀린에서는 Int와 같은 기본 타입들도 모두 클래스이다
  

- var은 일반 변수, val은 final 변수(불변 변수라고 하며 Immutable Variable)이다
  
</details>


---



# Chapter4
<details><summary>주요 내용
</summary>

## 리터럴의 타입

```kotlin
fun main(){
    val variable = 10 + 12 - 5 // 자동으로 타입을 유추한다
    println(variable)
 }
  
 ```
- 변수를 선언과 동시에 초기화하는 경우에 한해, 저장하려는 표현식으로부터 **타입을 추론**한다. 그래서 : Int와 같이 자료형을 표현해주는 코드를 생략할 수 있다  
  
</details>



---




# Chapter5
<details><summary>주요 내용
</summary>

## 산술 연산자(Arithmetic Operator) 

```kotlin
  fun main(){
    val num : Int = 15 -4 * 3
    val num2 : Int = 65%7
    val num3 : Double = 7.5/5 + 22.25
    val num4 : Double = num/num2 + 0.7

    println(num)
    println(num2)
    println(num3)
    println(num4)
}
```  
  
- `3/2 + 0.7` : 3과 2는 Int이기 때문에 1이 나오고 그 뒤에 0.7이 더해져 그때 Double이 된다
  
- 코틀린은 자바보다 더 **타입 체크에 엄격**하다 Double 타입의 변수에 Int 타입의 값을 저장할 수 없다  
- 또한, Double 타입의 변수에는 Double 타입인 표현식만 저장이 가능하므로 표현식이 조금 수정되어야 한다 (Int.toDouble()도 가능하다)
  
``` kotlin
  fun main(){
    val number : Int = 10 
    val num : Double = 15 + 7 / 2   //error
    val num2 : Double = 15.0 +7 / 2   // ok
    val num3 : Double = number.toDouble() + 7 / 2   //ok. 주의)number 자체가 변하는 것은 아니다
  }
```
  

  
  
</details>



---





# Chapter6
<details><summary>주요 내용
</summary>

## 증감 연산자(Increment & Decrement Operator)

```kotlin
  fun main(){
    var a = 10
    var b = 5
    println(a++ + b) // 15
    println(a) // 11
    println(--b) // 4
}
  
```  
 - 증감 연산자는 실제로 변수 값을 바꾸기 때문에 val이 아닌 var로 선언한다 
  
</details>



---




# Chapter7
<details><summary>주요 내용
</summary>

## 비트 연산자(Bitwise Operator) 
  
|형태|의미|자바에 대응하는 연산자|
|---|---|---|
|15 and 7|15와 7을 비트 단위로 and  연산|15 & 7|
|5 or 2 |5와 2를 비트 단위로 or 연산|15|2 |
||||
||||
||||
||||
||||  
  
</details>



---




# Chapter8
<details><summary>주요 내용
</summary>



  
  
  
</details>





---





# Chapter9
<details><summary>주요 내용
</summary>



  
  
  
</details>


---




# Chapter10
<details><summary>주요 내용
</summary>



  
  
  
</details>


---




# Chapter11
<details><summary>주요 내용
</summary>



  
  
  
</details>

---


# Chapter12
<details><summary>주요 내용
</summary>



  
  
  
</details>

---


# Chapter13
<details><summary>주요 내용
</summary>



  
  
  
</details>

---


# Chapter14
<details><summary>주요 내용
</summary>



  
  
  
</details>




---


# Chapter15
<details><summary>주요 내용
</summary>



  
  
  
</details>





---


# Chapter16
<details><summary>주요 내용
</summary>



  
  
  
</details>





---


# Chapter17
<details><summary>주요 내용
</summary>



  
  
  
</details>





---


# Chapter18
<details><summary>주요 내용
</summary>



  
  
  
</details>



---


# Chapter19
<details><summary>주요 내용
</summary>



  
  
  
</details>



---


# Chapter20
<details><summary>주요 내용
</summary>



  
  
  
</details>
