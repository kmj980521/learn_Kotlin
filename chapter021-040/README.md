# Chapter21 - if와 else의 중첩

<details><summary>주요 내용
</summary>

## if와 else의 중첩

</details>

---


# Chapter22 - if~else를 표현식으로 사용하기 
<details><summary>주요 내용
</summary>

## if~else를 표현식으로 사용하기 

 ```kotlin
  
  fun main(){

    val value : Int = if(10>5)
    {
        println("10은 5보다 크다")
        10
    }
    else
    {
        println("10은 5보다 크지 않다.")
        5
    }
    println(value) //10 
}
  
 ``` 

   
- if 블록과 else 블록의 마지막 표현식의 타입은 일치해야 한다 
- 만약 {} 블록이 비어있다면 Unit 타입이 되며 의미 없는 값이 저장된다 
- 이 표현식을 삼항 연산자처럼 사용 가능하므로 코틀린에서는 사함 연산자가 존재하지 않는다 
  
 

</details>


---


# Chapter23 - 흐름 제어 - 조건문 when
<details><summary>주요 내용
</summary>


## 흐름 제어 - 조건문 when
 
```kotlin
 
 when(타깃 표현식)
 {
  타깃 표현식과 비교할 값 -> { }
  타깃 표현식과 비교할 값2 -> { }
 }

``` 

 - 자바의 switch case를 업그레이드 한 버전이다.
 
 
 ```kotlin
 
 fun main(){
    val score : Int = 64

    when(score/10)
    {
        6 -> {println("D")}
        7 -> {println("C")}
        8 -> {println("B")}
        9,10 -> {println("A")}
        else -> println("F") // 실행문이 한 줄이라면 괄호생략 가능
    }
}
 
 ```
 
</details>


---



# Chapter24 - when을 표현식으로 사용하기 
<details><summary>주요 내용
</summary>

## when을 표현식으로 사용하기 

 ```kotlin
 
 fun main(){
    val score = 64
    
    val grade = when(score/10) {
        6 -> 'D'
        7 -> 'C'
        8 -> 'B'
        9, 10 -> 'A'
        else -> 'F'
    }
}
 
 ```
 
 ```kotlin
 
 val grade2 : Char = when{
        score >= 90 -> 'A'
        score >= 80 -> 'B'
        score >= 70 -> 'C'
        score >= 60 -> 'D'
        else -> 'F'
    }
 
 ```
 
 
 
 
  
</details>



---




# Chapter25 - 흐름 제어, 반복문 while
<details><summary>주요 내용
</summary>


## 흐름 제어 - 반복문 while
  
  
  
</details>



---





# Chapter26 - 흐름 제어, 반복문 do-while
<details><summary>주요 내용
</summary>


## 흐름 제어 - 반복문 do-while
  
  - 반드시 1번은 실행해야 할 때 사용
  
</details>



---




# Chapter27 - 흐름 제어, continue 
<details><summary>주요 내용
</summary>


## 흐름 제어 continue 
 
- continue 아래의 문장들은 모두 skip  
  
  
</details>



---




# Chapter28 - 흐름 제어, break
<details><summary>주요 내용
</summary>


## 흐름 제어 break
  
 - 특정 조건에 작성하며 break 키워드를 사용하면 반복문을 즉시 탈출할 수 있다
 
  
</details>





---





# Chapter29 - 레이블(Label)
<details><summary>주요 내용
</summary>

## 레이블(Label)
 
- break는 가장 가까운 반복문 '하나만' 빠져나온다. 이렇기 때문에 불필요한 코드가 들어갈 수도 있고 이를 방지하기 위해 코틀린에서는 **레이블(Label)** 이라는 문법을 제공한다 

- **name@** 을 while에 쓰고, break 바로 뒤에 **@name** 을 작성함으로써 실행 흐름을 제어한다
  
 ```kotlin
 
 fun main(){
    var x = 0
    var y = 0

    outer@ while(x<=20)
    {
        y = 0
        while(y<=20)
        {
            if(x+y==15 && x-y ==5)
            {
                break@outer
            }
            y+=1
        }
        x+=1
    }
    println("x:$x, y:$y")
}
 
 ```
 
 
  
  
</details>


---




# Chapter30 - 함수(Function)
<details><summary>주요 내용
</summary>

## 함수(Function)
 
 - 함수 속에 들어있던 문장들은 순차적으로 실행되며 이를 **함수 호출**이라고 부른다
 
 
```kotlin
 
 fun 식별자() : 반환 타입 {
  문장
 }
 
``` 

 ```kotlin
 
 fun main(){
    println(myFunction())
    println(myFunction()+10)
}

fun myFunction() : Int{
    val a = 3
    val b = 6
    println("a:" + a + ", b: " + b)
    return a+b 
}
 
 ```
 
 - 문장이 하나뿐인 블록은 =를 이용하여 줄여쓸 수 있으며 이 때 retun은 반드시 생략해야 하며 = 오른쪽은 함수의 반환 타입과 일치하는 표현식이 와야 한다 
 
 `fun function() : Double = 3.0 + 7`
 
 - 더 나아가, 아예 함수 반환 타입까지 생략할 수 있다
 
 `fun function() = 3.0 + 7`
  
</details>


---




# Chapter31 - 매개변수(Parameter)와 인수(Argument)
<details><summary>주요 내용
</summary>

## 매개변수(Parameter)와 인수(Argument)
 
- **매개변수(Parameter)** : 함수를 호출한 곳으로부터 값을 전달받을 때 사용
- **인수(Argument)** : 매개변수에 저장되는 표현식
 
- 매개변수를 선언할 때는 var이나 val 키워드를 붙이지 않는다. **매개변수는 무조건 val로 선언되므로 값을 수정할 수 없다**

 ```kotlin
 
 fun main(){
    println(cToF(30))
    println(getAverage(89,96))
}

fun cToF(celsius: Int) : Double {
    return celsius * 1.8 +32
}
fun getAverage(a: Int, b: Int) : Double{
    return (a+b)/2.0
}
 
 ```
  
  
</details>

---


# Chapter32 - Unit 타입
<details><summary>주요 내용
</summary>


## Unit 타입
 
 - 함수의 반환타입을 생략하면 자동으로 Unit이 된다
 - println의 반환 타입도 Unit이다 
 
 `fun celsiusToFash(celsius: Int) = println(celsius * 1.8 + 32)`
  
 - 자바의 void에 대응되는 개념이나 완전히 같은 것은 아니다
 - void는 반환 값이 없음을 의미하는 특수 타입이지만, Unit은 **class 키워드로 정의된 일반 타입** 이다 
 - Unit 타입을 반환하는 함수는, return을 생략한다고 해도 암묵적으로 Unit 타입의 객체를 retrun 하도록 되어 있고 그 Unit 객체는 **싱글톤 인스턴스** 이기 때문에 매번 객체를 생성하지는 않는다
  
</details>

---


# Chapter33 - 디폴트 인수
<details><summary>주요 내용
</summary>

## 디폴트 인수

 - 매개변수를 선언과 동시에 디폴트 값으로 초기화 
 - 함수를 호출하는 부분에서 인수를 설정해줄 수도 있다
 
```kotlin
 
 fun main(){
    println(getAverage(89,96))
    getAverage(100,50,true)
    println(getAverage(50))
    getAverage(66,print = true)
    getAverage(print = true)
    getAverage(print=true, a = 10, b= 30)
}

fun getAverage(a: Int = 0, b : Int = 0, print : Boolean = false) : Double {
    val result = (a+b) / 2.0
    if(print)
        println(result)
    return result
}
 
``` 
  
- 매개변수의 이름을 지정한 인수는 일반 인수들보다 항상 오른쪽에 있어야 한다 
 
```kotlin
 
 getAverage(print = true, 10, 30) // error
 getAverage(10, print = true, 30) // error
 
``` 
 
 
 
</details>

---


# Chapter34 - 가변 인수
<details><summary>주요 내용
</summary>

## 가변 인수

- 매개변수 앞에 **vararg 키워드** 를 붙인다  
  

 ```kotlin
 
 fun main(){
    println(getSumOf(1,2,3,4,5,6,7)) // 28
    println(getSumOf(32,57,12))      // 101
    println(getSumOf())              // 0
}

fun getSumOf(vararg numbers : Int) : Int{
    val size = numbers.size
    var i = 0; var sum = 0

    while(i<size)
    {
        sum+=numbers[i]
        i+=1
    }
    return sum
}
 
```               
                  
 - 가변 인수는 일반 인수와 함께 쓸 수도 있다
                  
 `fun function(something: Char, vararg numbers: Int): Int`
                  
 - 이 함수의 호출은 이와 같다
 
 `function(Char 타입 인수, N개의 Int 타입 인수) `
                  
 - 일반 인수가 가변 인수보다 오른쪽에 있으면 호출시 인수에 매개변수 이름을 붙여야 한다
                  
 `fun function(vararg numbers: Int, something: Char): Int `
                  
 - 이 함수의 호출은 이와 같다 
               
 `function(N개의 Int 타입 인수, something = Char 타입 인수)`
                  
                  
 ```kotlin
                 
    fun main(){
          test(1,2,3,4,5,something = 'C')        // number에 [1,2,3,4,5]가 들어간다
    }
    fun test(vararg number : Int, something : Char ): Int
       
    }             
                  
                  
 ```              
                  
 
 
</details>



---


# Chapter35 - 함수 오버로딩(Function Overloading)
<details><summary>주요 내용
</summary>

## 함수 오버로딩(Function Overloading)
 
- 이름이 같은 함수를 여러 개 선언하는 것 

  
  
  
</details>





---


# Chapter36 - 지역 변수(Local Variable)와 전역 변수(Global Variable)
<details><summary>주요 내용
</summary>


## 지역 변수(Local Variable)와 전역 변수(Global Variable)
  
 - **전역 변수** : 함수 밖에 선언한 변수이고 함수 호출이 끝나도 사라지지 않는다 
 
 - **지역 변수** : 함수 안에 선언한 변수이고 블록 밖으로 나가면 사라진다
 
 - **스코프(scope)** : 변수가 인식될 수 있는 범위
  
 
 
 
 
 
 
 
 
 
</details>





---


# Chapter37 - 지역 변수와 전역 변수의 이름이 중복될 때
<details><summary>주요 내용
</summary>


## 지역 변수와 전역 변수의 이름이 중복될 때
 
 
```kotlin
 
 var a = 5

fun main(){
    val a = 30
    println(a) // 가까운 scope에 있는 30을 출력한다 
    func()
}
fun func()
{
    println(a) // 5를 출력한다
}
 
``` 
 
 - 가장 가까운 스코프의 변수를 출력한다
 

  
</details>





---


# Chapter38 - 지역 변수와 다른 함수의 지역 변수가 중복될 때
<details><summary>주요 내용
</summary>

## 지역 변수와 다른 함수의 지역 변수가 중복될 때

 - 지역 변수 간에 스코프가 겹치지 않기 때문에 함수 간에 변수의 이름이 같아도 문제가 없다 
  
  
</details>



---


# Chapter39 - 지역 함수(Local Function)
<details><summary>주요 내용
</summary>


## 지역 함수(Local Function)
 
- **지역 함수** : 블록 안에 선언된 함수 
 
```kotlin
 
 fun main(){
    fun printFomular(a: Int = 20, b: Int){
        println(a * b + a - b)
    }

    printFomular(73,1)
    printFomular( b= 30)
}
 
``` 
 
 
  
  
</details>



---


# Chapter40 - 메모리의 스택(Stack) 영역
<details><summary>주요 내용
</summary>

## 메모리의 스택(Stack) 영역
 
- **스택(Stack)** : 지역 변수가 저장되는 공간. 차곡차곡 쌓인다
- 함수 호출 시 스택 영역에 해당 함수가 쌓이고 그 안의 변수들이 쌓이며 함수 호출 종료 시 스택 영역에서 사라진다
- main 함수가 끝나면서 모든 지역 변수가 스택 영역에서 사라진다

  
  
  
</details>

