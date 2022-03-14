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
|5 or 2 |5와 2를 비트 단위로 or 연산|15\|2 |
|15 xor 5|15와 5를 비트 단위로 xor 연산| 15^5|
|32767.inv()|32767을 비트 단위로 반전|~32767|
|1 shl 3|1을 왼쪽으로 3칸 시프트|1 <<3|
|8 shl 1|8을 오른쪽으로 1칸 시프트| 8 >> 1|
|~17 ushr 2|부호를 유지한채 -17을 오른쪽으로 2칸 시프트 | - 17>>>2|  
  
```kotlin
  fun main(){
    println(15 and 7) // 7
    println(5 or 2)   // 7
    println(15 xor 5) // 10
    println(32767.inv()) // -32768
    println(1 shl 3) //8
    println(8 shr 1) // 4
    println(-17 ushr 2) // 1073741819
}
```  
  
  
</details>



---




# Chapter8
<details><summary>주요 내용
</summary>

## 정수 타입과 실수 타입

|종류| 타입 | 용량(단위:Byte) | 저장 가능 범위 |
|---|---|---|---|
|정수 타입| Byte | 1| -128~127|
|| Short|2|-3만 2768~3만 2767|
|| Int|4|-21억 4748만 3648~21억 4748만 3647|
|| Long|8|-922경 3372조 0368억 5477만 5808~922경 3372조 0368억 5477만 5807|
|실수 타입|Float|4|1.410-45~3.40282351038|
||Double|8|4.910-324~1.797693134862315710308|
 
- 성적 처리 프로그램처럼 매우 작은 수를 처리할 때는 학생 개개인의 점수(0~100)를 Byte 타입으로 사용해 효율적으로 용량을 사용한다 
  
 ## 컴퓨터의 실수 표현  
- 컴퓨터는 표현하려는 실수 값을 항상 1.xxxxx 형태로 만든다
- 표현하려는 수가 2진수로 1011.1001일 경우 1.0111001로 변환하고 뒤에 2^-3을 곱해 소수점의 위치를 왼쪽으로 3칸 이동시킨다. 이때 유효숫자인 10111001와 지수 부분인 -3만을 저장한다 
- 이를 **부동소수점(Floating Point)** 방식이라고 한다
  
  
  
```kotlin
  fun main(){
    val a : Byte = 125
    val b : Short = (100+200) * 100
    var c : Int = 12_4354_6538
    c = 0xFF_88_88
    c = 0b01010010_01100011_01110101_01000101
    var d:Long = -543_7847_3984_7238_4723

    c = a+b
    d = c+10L

    var e: Float = 67.6f
    val f : Double = 658.456
    e = (e + f).toFloat()
    println(e)
}
```  

- 정수 리터럴이 **0x** 로 시작하면, 뒤이어 오는 수가 16진수로 인식된다. 
- 정수 리터럴이 **0b** 로 시작하면, 뒤이어 오는 수가 2진수로 인식된다. 
  
- Int 타입보다 작은 정수 타입들(Byte, Short)끼리 **어떤 산술 연산을 해도 무조건 Int 타입이 나온다** . 즉, Byte + Byte, Short - Short, Short / Byte 모두 Int 타입이 된다  
  
- 정수 리터럴 뒤에 L을 붙이면, 그 리터럴은 수의 크기에 상관 없이 무조건 Long 타입이 된다
  실수 리터럴 뒤에 f를 붙이면 그 리터럴은 Float 타입이 된다
  
</details>





---





# Chapter9
<details><summary>주요 내용
</summary>


## 실수 타입의 함정
  
```kotlin
  
  fun main(){
    println(0.1f+0.1f+0.1f) //0.3
    println(0.1f+0.1f+0.1f+0.1f+0.1f+0.1f+0.1f+0.1f+0.1f+0.1f) // 1.00000001 -> 엉뚱한 값이 나온다
    println(0.1f*10) // 1.0
}
```  
 
  - 실수 값은 2신수 유효숫자로 표현되기 때문에 **상황에 따라 정확한 값을 가리킬 수 없다**
  
  
  
</details>


---




# Chapter10
<details><summary>주요 내용
</summary>

## 문자 타입
  
```kotlin
  
  fun main(args:Array<String>) : Unit {
    var ch : Char = 'A'
    println(ch) //A

    ch = '\uAC00'
    println(ch) //가

    ch = '한'
    println(ch.toInt()) //54620
    println(ch.code) // -> code로 바뀌었다 
}
  
```
  
 - 코틀린에서는 **유니코드(Unicode)** 를 사용한다
 - 유니코드의 범위는 0~65535이다 

  
  
  
</details>


---




# Chapter11
<details><summary>주요 내용
</summary>


## 문자열(String)
  
  ```kotlin
  
  fun main(){
    var str: String = "Hello"
    println(str) // Hello

    str = str + "\nKotlin!"
    println(str) // Hello\nKotlin

    println(str[8]) //t

    val num = 10 * 5 + 3
    println(str + num) //Hello\nKotlin!53
}
  
  ```
  
  - +연산자의 양 피연산자가 String 타입이면, 왼쪽의 문자열에 오른쪽의 문자열을 덧붙이는 concat 연산을 한다 
  
  `println("Great"[1]) ` : r이 출력된다
  
  
  - String과 String이 아닌 값을 + 연산자로 연결하면, String이 아닌 값을 String으로 변환한 뒤 서로 합친다.
  
</details>

---


# Chapter12
<details><summary>주요 내용
</summary>

## 문자열 안에 표현식의 값을 집어넣기 
- **$ 키워트**를 사용하며, $ 뒤에 변수 이름을 적으면 해당 부분은 변수의 값으로 대체된다
- $ 자체를 출력하고자 할 때는 \$를 대신 사용한다
  
  ```kotlin
  fun main(){
    val a : Int = 10
    val b = 20

    println("a의 값: $a")
    println("b의 값: $b")

    println("a+b의 값 = ${a+b}")
}
  
  ```
  
  
</details>

---


# Chapter13
<details><summary>주요 내용
</summary>


1
  
  
  
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
