# Chapter21

<details><summary>주요 내용
</summary>

## if와 else의 중첩

</details>

---


# Chapter22
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


# Chapter23
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



# Chapter24
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




# Chapter25
<details><summary>주요 내용
</summary>


## 흐름 제어 - 반복문 while
  
  
  
</details>



---





# Chapter26
<details><summary>주요 내용
</summary>


## 흐름 제어 - 반복문 do-while
  
  - 반드시 1번은 실행해야 할 때 사용
  
</details>



---




# Chapter27
<details><summary>주요 내용
</summary>


## 흐름 제어 continue 
 
- continue 아래의 문장들은 모두 skip  
  
  
</details>



---




# Chapter28
<details><summary>주요 내용
</summary>


## 흐름 제어 break
  
 - 특정 조건에 작성하며 break 키워드를 사용하면 반복문을 즉시 탈출할 수 있다
 
  
</details>





---





# Chapter29
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




# Chapter30
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




# Chapter31
<details><summary>주요 내용
</summary>



  
  
  
</details>

---


# Chapter32
<details><summary>주요 내용
</summary>



  
  
  
</details>

---


# Chapter33
<details><summary>주요 내용
</summary>



  
  
  
</details>

---


# Chapter34
<details><summary>주요 내용
</summary>



  
  
  
</details>




---


# Chapter35
<details><summary>주요 내용
</summary>



  
  
  
</details>





---


# Chapter36
<details><summary>주요 내용
</summary>



  
  
  
</details>





---


# Chapter37
<details><summary>주요 내용
</summary>



  
  
  
</details>





---


# Chapter38
<details><summary>주요 내용
</summary>



  
  
  
</details>



---


# Chapter39
<details><summary>주요 내용
</summary>



  
  
  
</details>



---


# Chapter40
<details><summary>주요 내용
</summary>



  
  
  
</details>

