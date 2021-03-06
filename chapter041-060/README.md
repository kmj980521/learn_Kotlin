# Chapter41 - 소스 파일 여러 개로 분리하기

<details><summary> 주요 내용
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




# Chapter48 - 힙 영역의 존재 이유 
<details><summary>주요 내용
</summary>


## 힙 영역의 존재 이유 
  
- 어느 블록에서 생성했던 간에, 블록을 빠져나와도 지워지지 않는다 
- 인스턴스의 참조값을 활용할 때 두 개의 참조 변수가 하나의 객체를 가리키게 해서 **하나의 객체를 여러 참조 변수에서 공유하는 형태**로 사용할 수 있어 메모리 공간을 절약할 수 있다
  
</details>





---





# Chapter49 - 문자열간 + 연산 시 주의점
<details><summary>주요 내용
</summary>

## 문자열간 + 연산 시 주의점

 - 실제 문자열은 힙 영역에 생성되먀, String 변수는 문자열의 참조값을 저장하기 위한 공간만 갖고 있다. 
 - 두 문자열을 이어 붙이면 원래 갖고 있던 문자열에 새로운 문자열이 덧붙여지는 게 아니라, 기존의 문자열은 그대로 남고 합쳐진 문자열이 새로 생성된다  
 - 그렇다면 기존의 문자열은 그대로 남아있을까? 
  
</details>


---




# Chapter50 - 가비지 컬렉션(Garbage Collection)
<details><summary>주요 내용
</summary>

## 가비지 컬렉션(Garbage Collection)

- 미아가 된 객체들이 메모리 공간이 부족해질 정도까지 쌓이면 가비지 컬렉션 기능에 의해 소멸되고 메모리를 효율적으로 사용하게 한다   
- **프리징** : 가비지 컬렉션이 일어날 때 삭제할 미아 객체들을 탐색해야 하기 때문에 순간적으로 프로그램이 멈추는 현상  
  
</details>


---




# Chapter51 - ===, !== 연산자
<details><summary>주요 내용
</summary>

## ===, !== 연산자

- **===** : 두 참조 변수가 같은 객체를 가리킬 때 true, 아니라면 false 
- **!==** : 두 참조 변수가 다른 객체를 가리킬 때 true, 아니라면 false 
  
```kotlin
  
  fun main(){
    var a : Person = Person()
    var b : Person = a

    println(a===b) // true
    b = Person()
    println(a===b) // false
    println(a!==b) // true
}
  
- 코틀린에서의 == 연산자는 자바의 equals 메서드를 호출한 것과 같은 효과를 지닌다  
  
  
```  
  
  
  
  
</details>

---


# Chapter52 - 멤버 함수(Member Function)
<details><summary>주요 내용
</summary>

## 멤버 함수(Member Function)
  
- **멤버 함수** : 클래스에 내장된 함수  
- 특정 클래스와 강한 연관이 있는 함수는 아예 클래스 안으로 내장시킨다
- 멤버 함수가 객체의 **동작 역할** 을 한다
  
```kotlin
  
  class ch052 {
    var name : String = ""
    var date = ""
    var area = 0

    fun print():Unit {
        println("name = ${this.name}")
        println("date = ${this.date}")
        println("area = ${this.area}")
    }
}
  
```  
  
</details>

---


# Chapter53 - 프로퍼티와 멤버 함수의 매개변수 이름이 중복될 때
<details><summary>주요 내용
</summary>

## 프로퍼티와 멤버 함수의 매개변수 이름이 중복될 때

```kotlin
  
  class ch053{
    var num : Int = 50

    fun print(num : Int)
    {
        println(num) // 100 
        println(this.num) // 50
    }
}

fun main(){
    val a = ch053()
    a.print(100)
}
  
```  
  
- 중복된 값이 존재한다면 **this 키워드** 를 사용하여 구분한다  
  
</details>

---


# Chapter54 - 생성자(Constructor)와 초기화(Initializer) 블록
<details><summary>주요 내용
</summary>

## 생성자(Constructor)와 초기화(Initializer) 블록

  
-  `class 클래스 이름 constructor(생성자의 매개변수 선언) {...}`
- **init 블록** 내부에서 생성자의 매개변수를 사용한다
- 코틀린에서는 생성자 정의부를 아예 클래스 이름에 합쳐버렸다   

```kotlin
  
  class Subway constructor(name:String, line:Int){
    val name : String 
    val line : Int 
    
    init{
        this.name = name 
        this.line = line 
    }
}
  
  fun main(){
    val subway1 : Subway = Subway("신분당선",1)
    println(subway1.line)
}
  
  
```  
  
 - constructor 키워드를 생략해도 상관 없다 
  
</details>




---


# Chapter55 - init 블록 나누어 쓰기
<details><summary>주요 내용
</summary>

## init 블록 나누어 쓰기 

- 인스턴스가 생성된다고 해서 init 블록이 곧장 실행되는 것은 아니다.
- **위에서부터 순서대로** 프로퍼티의 선언 및 초기화문과, init 블록이 실행된다
  
 ```kotlin
  
  class Size(width:Int, height: Int){
    val width : Int 
    val height : Int 
    
    init{
        this.width = width
        this.height = height
    }
    val area : Int 
    
    init{
        this.area = this.width * this.height
    }
}
  
 ``` 
  
  
  
  
</details>





---


# Chapter56 - 생성자와 프로퍼티 한번에 쓰기
<details><summary>주요 내용
</summary>

## 생성자와 프로퍼티 한번에 쓰기

``` kotlin
  
  class Car(val name: String, val speed: Int = 0)
  
```  
- 생성자 매개변수 앞에 val이나 var 키워드를 붙이면, 동일한 이름의 프로퍼티가 같이 선언된다  
  
</details>





---


# Chapter57 - 보조 생성자(Secondary Constructor)
<details><summary>주요 내용
</summary>

## 보조 생성자(Secondary Constructor)
  
- **주 생성자(Primary Constructor)** : 클래스 이름 옆에 오는 생성자 
- **보조 생성자(Secondary Constructor)** : 클래스 내부에 오는 생성자 

 ```kotlin
  
  class 클래스 이름 constructor(매개변수)
  {
    constructor(매개변수):this(인수)
    {
      ....
    }
  }
  
 ```
  
 ```kotlin
  
  class Time(val second:Int) // second는 공통적으로 가진다
{
    init{
        println("init 실행")
    }
    constructor(minute:Int,second:Int) : this(minute*60 + second){
        println("보조 생성자 1 실행 중 ")
    }
    constructor(hour:Int,minute:Int,second:Int) : this(hour*60+minute,second){
        println("보조 생성자 2 실행 중")
    }
    init {
        println("또 다른 init 블록 실행")
    }
}
fun main(){
    println("${Time(15,6).second } 초")
    println("${Time(6,3,17).second} 초")
}
  
 ``` 
  
  - 여기에서 this는 이 클래스에 포함된 또 다른 생성자를 호출하는 문법 
  
 ![image](https://user-images.githubusercontent.com/61898890/158727225-5bd81105-ee4b-4e34-b53e-ff2f2b57172f.png)

 - 2번째 경우는 보조 생성자 2를 호출, 보조 생성자 2에서 보조 생성자 1을 호출, 보조 생성자 1에서 주 생성자를 호출하기 때문에 이와 같은 과정이 된다  
  
 - 보조 생성자는 다시 주 생성자를 먼저 호출하므로,  **궁극적으로는 주 생성자가 가장 먼저 호출되게 한다** 
 
  
  
</details>





---


# Chapter58 - 프로퍼티와 Getter/Setter
<details><summary>주요 내용
</summary>

## 프로퍼티와 Getter/Setter

- 특정 객체의 프로퍼티에 특정 값을 대입하면, 이 프로퍼티에 해당하는 setter가 호출된다  
- **field 식별자** : 실제로 값이 저장되는 프로퍼티 속의 변수를 나타내는 특수 식별자   
- val 프로퍼티는 초기 값이 주어지면 더 이상 값을 변경할 수 없기 때문에 Getter만 존재한다 
- 프로퍼티에 **디폴트 Getter/Setter 가 포함되어 있따 **  

  
   
 
|용어|의미|
|---|---|
|Field|실제로 데이터가 저장되는 공간|
|Getter| 저장된 값을 읽으려고 할 때 호출되는 함수|
|Setter| 값을 저장하려고 할 때 호출되는 함수|
  
```kotlin
  
  class Per{
    var age : Int = 0
    get(){
        return field
    }
    set(value){
        field = if(value>0) value else 0
    }
}
fun main(){
    val per : Per = Per()

    per.age = -30
    println(per.age) // 0
}

```  
  
  
  
</details>



---


# Chapter59 - 연산자 오버로딩(Operator Overloading)
<details><summary>주요 내용
</summary>

## 연산자 오버로딩(Operator Overloading)

- 연산자 오버로딩을 정의해 두 객체끼리의 덧셈을 구현할 수 있다  

- 멤버 함수 정의문 앞에 **operator를 붙인다** : 인스턴스 간에 연산자를 사용했을 때 이 멤버 함수를 대신 호출해달라는 의미이다   

  
```kotlin
  
  class Point(var x : Int = 0, var y : Int = 0)
{
    operator fun plus(other: Point) : Point{
        return Point(x+other.x, y+other.y)
    }
    operator fun minus(other: Point) : Point{
        return Point(x-other.x, y-other.y)
    }
    operator fun times(number : Int) : Point {
        return Point(x * number, y * number)
    }
    operator fun div(number : Int) : Point {
        return Point(x / number, y/number)
    }
    fun print(){
        println("x : $x, y : $y")
    }
}
fun main(){
    val pt1 = Point(3,7)
    val pt2 = Point(2,-6)

    val pt3 = pt1 + pt2
    val pt4 = pt3 * 6
    val pt5 = pt4 / 3
    pt3.print()
    pt4.print()
    pt5.print()
}
  
```  
  
  
  
  
</details>



---


# Chapter60 - 번호 붙은 접근 연산자(Indexed Access Operator) []
<details><summary>주요 내용
</summary>


## 번호 붙은 접근 연산자(Indexed Access Operator) []
  
- **Getter/Setter를 operator 키워드를 사용해 재정의 ** 한다. (when을 사용한다)
 
```kotlin
  
  class Pers(var name : String, var birthday : String)
{
    operator fun get(position: Int) : String {
        return when(position)
        {
            0 -> name
            1 -> birthday
            else -> "알 수 없음"
        }
    }
    operator fun set(position: Int, value : String){
        when(position)
        {
            0 -> name = value
            1 -> birthday = value 
        }
    }
}
  
```  

- []연산자에는 여러 개의 피연산자를 지정할 수 있다. 

`pers[1,2,3] -> pers.get(1,2,3)` 
  
`pers[1,2] = "J" -> pers.set(1,2,"J")`
  
</details>


