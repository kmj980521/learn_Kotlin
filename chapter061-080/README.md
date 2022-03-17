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
  
  
  
</details>


---




# Chapter71
<details><summary>주요 내용
</summary>



  
  
  
</details>

---


# Chapter72
<details><summary>주요 내용
</summary>



  
  
  
</details>

---


# Chapter73
<details><summary>주요 내용
</summary>



  
  
  
</details>

---


# Chapter74
<details><summary>주요 내용
</summary>



  
  
  
</details>




---


# Chapter75
<details><summary>주요 내용
</summary>



  
  
  
</details>





---


# Chapter76
<details><summary>주요 내용
</summary>



  
  
  
</details>





---


# Chapter77
<details><summary>주요 내용
</summary>



  
  
  
</details>





---


# Chapter78
<details><summary>주요 내용
</summary>



  
  
  
</details>



---


# Chapter79
<details><summary>주요 내용
</summary>



  
  
  
</details>



---


# Chapter80
<details><summary>주요 내용
</summary>



  
  
  
</details>



