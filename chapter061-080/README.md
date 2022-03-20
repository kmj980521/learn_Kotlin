# Chapter61 - 호출 연산자(Invoke Operator) ()

<details><summary>주요 내용
</summary>

## 호출 연산자(Invoke Operator) ()
  
 ```kotlin
  
  class Product(val id: Int, val name: String)
{
    operator fun invoke(value:Int)
    {
        println(value)
        println("id:$id\nname:$name")
    }
}
fun main(){
    var a = Product(762443, "코틀린 200제")
    a(100) // 컴파일 시 a.invoke(100)으로 번역된다
}
  
 ``` 
  

</details>

---


# Chapter62 - in 연산자
<details><summary>주요 내용
</summary>


## in 연산자
  
- **in 연산자** : 어떤 값이 객체에 포함되어 있는지 여부를 조사  
  
```kotlin
  
  fun main(){
    println('o' in "Kotlin") // true
    println("in" !in "Kotlin") // false
}
  
- String 클래스에는 Char 타입을 인수로 받는 contains와, String 타입을 인수로 받는 contains가 존재한다
  
- in 연산자는 `operator fun contains(매개변수:타입) : Boolean` 멤버 함수로 오버로딩 할 수 있다. 

- in 연산자는 when 문에서도 쓸 수 있다
  
```  
  
  
  
</details>


---


# Chapter63 - 멤버 함수의 중위 표기법(Infix Notation)
<details><summary>주요 내용
</summary>

## 멤버 함수의 중위 표기법(Infix Notation)

- **중위 표기법(Infix Notation)** : 피연산자 연산자 피연산자의 순서로 표현식을 구성하는 방식. 멤버 함수의 매개변수가 하나뿐이면 함수 호출을 중위 표기법으로 할 수 있다
  
- 멤버 함수 선언문 앞에 infix를 붙인다 
  
 ```kotlin
  
  class Point(var x:Int = 0, var y:Int = 0)
{
    infix fun from(base:Point): Point{
        return Point(x-base.x, y-base.y)
    }
}

fun main(){
    val pt = Point(3,6) from (1,1)
    println(pt.x) // 2
    println(pt.y) // 5
}
  
 ``` 
  
  
  
</details>


---



# Chapter64 - 상속(Inheritance)
<details><summary>주요 내용
</summary>

## 상속(Inheritance)

- 기존에 존재하는 클래스를 확장하여 새로운 클래스를 정의하는 기법 
  
- 코틀린은 클래스 선언이 **기본적으로 final로 되어 있어** 상속을 허용하려면, 클래스 정의부 앞에 **open 키워드** 를 붙인다 

```kotlin
  
  open class Person(val name:String, val age:Int)

class Student(name:String, age: Int, val id: Int) : Person(name,age)

fun main(){
    val person = Person("홍길동",35)
    val student = Student("김길동",23,20171217)
}
  
```  
  
- **슈퍼클래스(Superclass)** : 상속의 대상이 되는 클래스
- **서브클래스(Subclass)** : 상속하여 확장된 클래스 
  
- 상속 문법
 
` class 클래스 이름: 슈퍼클래스 생성자(인수) {...} ` 
  
- **상속은 하나의 클래스만 할 수 있다**  
  
</details>



---




# Chapter65 - 업캐스팅(Upcasting)
<details><summary>주요 내용
</summary>

## 업캐스팅(Upcasting)

- **캐스팅(Casting)** : 특정 타입을 다른 타입으로 변환하는 것 
  
- 업캐스팅 : 서브클래스의 인스턴스를 슈퍼클래스 타입으로 가리키는 것   
  
 ```kotlin
  
open class Person2(val name:String, val age:Int)

class Student2(name:String, age: Int, val id: Int) : Person2(name,age)

fun main(){
    val person : Person2 = Student2("John",32,20171218)
}
  
 ``` 
- 참조 변수는 Student의 인스턴스를 가리키고 있기는 하지만, 타입이 상위클래스인 Person2이기 때문에 id 프로퍼티에는 접근을 하지 못한다 
 
- **슈퍼클래스 타입은 항상 슈퍼클래스 자체나 서브클래스의 인스턴스만 가리킬 수 있다** 

- **다형성(Polymorphsim)** : 한 객체가 여러가지 타입을 가질 수 있는 성질 
  
</details>



---





# Chapter66 - 오버라이딩(Overriding)
<details><summary>주요 내용
</summary>

## 오버라이딩(Overriding)
  
- 슈퍼클래스의 멤버 함수와 시그니처가 동일한 멤버 함수를 서브클래스에서 선언하면, 슈퍼클래스 멤버 함수의 동작을 덮어쓰기 한다
  
- 멤버 함수도 클래스와 마찬가지로 오버라이딩을 허용하려면 **open 키워드** 를 사용한다 

```kotlin
  
  open class AAA
{
    open fun func() = println("AAA")
}

class BBB : AAA(){
    override fun func(){
        super.func()
        println("BBB")
    }
}

fun main(){
    AAA().func()
    BBB().func()
}
  
```  
  
- 서브클래스에서 재정의하고자 하는 메서드는 **override 키워드** 를 붙인다   
  
- 만약 멤버 함수의 재 오버라이딩을 막으려면 **final 키워드** 를 붙인다   

</details>



---




# Chapter67 - 프로퍼티를 오버라이딩하기
<details><summary>주요 내용
</summary>


## 프로퍼티를 오버라이딩하기
  
 
  
```kotlin
  
  open class A{
    open var number : Int = 10
    get(){
        println("A의 getter")
        return field
    }
    set(value){
        println("A의 setter")
        field = value
    }
}

class B : A(){
    override var number : Int
    get(){
        println("B의 getter")
        return super.number
    }
    set(value) {
        println("B의 setter")
        super.number = value
    }
}
fun main(){
    val test = B()
    test.number= 5
    test.number
}
  
```  
  
![image](https://user-images.githubusercontent.com/61898890/158757666-9096dce3-8692-4052-9dff-5c7bb1a96f96.png)
  
  
- 프로퍼티를 오버라이딩할 때도 **override 키워드** 를 붙인다   
  
</details>



---




# Chapter68 - 다형성(Polymorphism)의 활용
<details><summary>주요 내용
</summary>


## 다형성(Polymorphism)의 활용
  
```kotlin
  
  open class AA{
    open fun hello() = println("AA의 hello")
}
class BB:AA(){
    override fun hello() = println("BB의 hello")
}

fun main(){
    val one = AA()
    val two = BB()
    val three:AA = two

    one.hello() // AA의 hello 
    two.hello() // BB의 hello 
    three.hello() //BB의 hello
}
  
```  
  
- 멤버 함수를 호출할 때, 참조 변수가 **실제로 가리키고 있는 객체의 멤버 함수가 호출된다**  
  
</details>





---





# Chapter69 - 클래스를 상속하는 객체
<details><summary>주요 내용
</summary>


## 클래스를 상속하는 객체 
  
```kotlin
  
  open class a1(val name: String, val age: Int)
{
    open fun print(){
        println(name)
        println(age)
    }
}

fun main(){
    val custom : a1 = object : a1("Alan",23)
    {
        override fun print(){
            println("It's a object")
        }
    }
    custom.print()
}
  
```  
  
- 클래스 없이 객체를 만들면서 상속을 했으므로 이때의 상속은 1회용이 된다   
  
  
</details>


---




# Chapter70 - Any 클래스
<details><summary>주요 내용
</summary>


## Any 클래스
  
 - 어떤 클래스가 아무 클래스도 상속하지 않으면 **자동으로 Any 라는 클래스를 상속한다**
 
 - 모든 코틀린 클래스들은 Any 클래스를 상속한다는 것이 보장된다 
  
 - Any Class
  
 ```kotlin
  
  open operator fun equals(other: Any?): Boolean // == 연산자를 오버로딩하는 멤버 변수 
  open fun hashCode(): Int // 객체 고유의 해시코드를 반환하는 멤버 함수 
  open fun toString(): String // 객체의 내용을 String 타입으로 변환하는 멤버 함수 
  
 ``` 
  

 ```kotlin
  
  class Building(var name:String = "", val date: String ="", val area : Int = 0 )
{
    override fun toString(): String =
        "이름:${this.name}\n"+
        "건축일자:${this.date}\n"+
        "면적:${this.area}"

}

fun main(){
    val building = Building("코틀린","20101010",area=100)
    printObject(building)
    println(building)
}
fun printObject(any:Any)
{
    println(any.toString())
}
  
 ``` 
  
![image](https://user-images.githubusercontent.com/61898890/158765282-9e28c095-381f-435b-ab39-3854fe8cd2b0.png)
 
  
  
</details>


---




# Chapter71 - 예외(Exception)
<details><summary>주요 내용
</summary>


## 예외(Exception)
 
- 프로그램 실행 중 예상치 못하게 발생한 상황
  
  
  
</details>

---


# Chapter72 - 예외 처리
<details><summary>주요 내용
</summary>

## 예외 처리

- try~catch~finally 블록을 사용한다 

- try 블록에는 예외가 발생할 가능성이 있는 부분을 감싸준다

- catch 블록에는 예외가 발생했을 때 대신 실행할 코드를 지정한다 
  
- finally 블록에는 예외 발생 여부와 상관 없이 무조건 실행되는 블록이다
  
```kotlin
  
  fun main(){
    try{
        val str= "abcd"
        val num = str.toInt()
    }catch (e: NumberFormatException){
        println(e)
    }finally{
        println("finally")
    }
}
 
```
  
![image](https://user-images.githubusercontent.com/61898890/159156778-ae3ce6c6-0bcd-4f5a-a244-dd288df2a5d8.png)
  
  
  
</details>

---


# Chapter73 - 예외 던지기
<details><summary>주요 내용
</summary>

## 예외 던지기 

- `throw Throwable타입 표현식`   
  
```kotlin
  
      try{
        something()
    }catch(e:Exception){
        println(e.message)
    }
}
fun something(){
    val num1 = 10
    val num2 = 0
    div(num1, num2)
}

fun div(a:Int, b:Int) : Int
{
    if(b==0)
        throw Exception("DivisionError")
    return a/b
}
  
``` 
  
- 코틀린은 throws 키워드를 제거해 예외 처리는 필수가 아닌 옵션으로 했다   
  
</details>

---


# Chapter74 - Nothing 타입
<details><summary>주요 내용
</summary>

## Nothing 타입

- **Nothing 타입** : 실행 흐름이 도달할 수 없는 구역  
  
```kotlin
  
  fun throwing(): Nothing = throw Exception()

fun main(){
    println("start")
    val i : Int = throwing()
    print(i)
}
  
```  
  
  
- thorw Exception()은 Nothing 타입의 표현식이기 때문에 if-else 블록이 Int 타입의 표현식으로 인식된다. 만약 throw Exception 부분이 표현식이 아니었다면, else 블록의 타입이 Unit이 되어버리므로 if-else를 표현식으로 쓸 수 없게 된다.
  
- **Nothing 타입은 throw를 표현식으로 쓸 수 있게 하기 위한 장치**
  
</details>




---


# Chapter75 - Nullable 타입과 null
<details><summary>주요 내용
</summary>

## Nullable 타입과 null

  - 타입 이름 뒤에 **? 키워드** 를 붙이면 변수를 Nullable하게 만들 수 있다
  - **Nullable** : null 값을 지정할 수 있는 변수 
  
  - null은 Nothing? 타입의 표현식이다
  
  - Byte, Short, Int, Long, Float, Double, Char, Boolean 타입 뒤에 ?를 붙이면 그 변수는 **참조 변수**가 된다
  
  - 코틀린에서는 Nullable 타입이 아니면 null을 지정할 수 없다
  
  ```kotlin
  
  fun main(){
    var num : Int? = null
    num = 10
    num = null
  }
  
  ```
  
  
</details>





---


# Chapter76 - 안전한 호출 연산자(Safe Call Operator) ?.
<details><summary>주요 내용
</summary>

## 안전한 호출 연산자(Safe Call Operator) ?.
  
- Nullable한 참조 변수의 프로퍼티와 멤버 함수에 접근하려면,   **. 대신 ?.** 연산자를 반드시 사용해야 한다

- `참조 변수?.프로퍼티` : 참조 변수가 null이면 이 표현식이 null 값을 갖게 된다 
  
- `참조 변수?.멤버 함수()` : 참조 변수가 null이면 멤버 함수를 호출하지 않고 표현식은 null이 된다
  
```kotlin
  
  fun main(){
    var obj:Building? = null
    println(obj?.toString()) // 표현식의 값은 null, 타입은 Unit?이 된다
    obj?.name = "건물" // Getter/Setter이나 null이기 때문에 위와 비슷하게 작동한다

    obj = Building()
    obj?.name = "서울 월드컵 경기장"
    obj?.date = "2001년 11월 10일"
    obj?.area = 21_6712
    println(obj?.toString())
}
  
```  
  
  
  
  
</details>





---


# Chapter77 - Not-null 단정 연산자(Not-null Assertion Operator) !!
<details><summary>주요 내용
</summary>

## Not-null 단정 연산자(Not-null Assertion Operator) !!

- **!! 연산자** : Nullable 타입을 Not-null 타입으로 강제로 캐스팅한다 
  
```kotlin
  
  fun main(){
    var obj: Building? = Building()
    obj!!.name = "서울시장" // obj는 null이 아닐 것이다! 라고 단정을 지음
    println(obj!!.name)

    obj = null
    print(obj!!.toString())
}
  
```  
  
![image](https://user-images.githubusercontent.com/61898890/159159089-1dce38f3-96cc-4ff4-998d-6d1552045621.png)
  
- null이면 NullPointerException이 발생한다  
  
</details>





---


# Chapter78 - 엘비스 연산자(Elvis Operator) ?:
<details><summary>주요 내용
</summary>

## 엘비스 연산자(Elvis Operator) ?:

- **왼쪽의 피연산자가 null이 아니면 그 값을 그대로 쓰고, null이면 우측의 피연산자로 대체한다**  
  
``` kotlin
  
  fun main(){
    val number: Int? = null // number는 nullable
    println(number ?: 0)

    val number2: Int? = 15
    println(number2 ?: 0)
}  
  
- 코틀린의 간편함  
  
```java  
  
  String str;
  ....
  return (str != null) ? str : "Hello";
  
```  
  
```kotlin
  
 return str ?: "Hello" 
  
``` 
  
  
</details>



---


# Chapter79 - 스마트 캐스팅
<details><summary>주요 내용
</summary>


  
## 스마트 캐스팅 

- **스마트 캐스팅(Smart Casting)** : 특정 조건을 만족하는 경우, 컴파일러는 변수의 타입을 다른 타입으로 자동 캐스팅  
  
```kotlin
  
  fun main(){
    val number:Int ? = null
    val number2 = 1225

    checkNull(number)
    checkNull(number2)
}
fun checkNull(any:Any?){
    if(any==null)
    {
        println("Null값")
        return
    }
    println(any.toString()) // 위의 if를 통과하면 null이 아닐 것이라 완벽하게 추론해낼 것이라 ?.을 사용하지 않아도 된다!
}
  
```  
  
- 위의 if를 통과하면 null이 아닐 것이라 완벽하게 추론해낼 것이라 ?.을 사용하지 않아도 된다!
  
  
  
</details>



---


# Chapter80 - is 연산자
<details><summary>주요 내용
</summary>

## is 연산자

- 참조 변수가 **실제로 가리키고 있는 객체의 타입** 을 알아낸다   
  
- 코틀린의 is 연산자는 자바의 instanceof에 해당한다 
  
```kotlin
  
  fun main(){
    val person: Person = Student("Mark Zuckerberg", 33, 20171225)
    println("${person is Person}") // true 
    println("${person is Student}") // true 
    println("${person is Professor}") // false 


    val person2: Person = Professor("Kim", 48)
    println("${person2 is Person}") // true 
    println("${person2 is Student}") // false 
    println("${person2 is Professor}") // true
}
  
```  
 
- is와 when의 활용 
  
```kotlin
  
  val person:Person
    ... 
    when(person){
        is Person -> {}
        is Student -> {}
        is Professor -> {}
    }
  
```  
  
  
  
</details>



