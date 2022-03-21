# Chapter81 - as 연산자와 다운캐스팅

<details><summary>주요 내용
</summary>

## as 연산자와 다운캐스팅

- **다운캐스팅(Downcasting)** : 업캐스팅과 반대로 슈퍼클래스 타입을 서브클래스 타입으로 받는 것  
  
- `피연산자(참조 변수) as 피연산자(타입)` : 왼쪽 피연산자의 타입을 오른쪽 피연산자 타입으로 캐스팅  
  
- `person as Student`   
  
- 캐스팅에 실패했을 때 예외가 발생하는 것을 막고 싶으면 **as? 연산자** 를 대신 사용해야 한다  
  
</details>

---


# Chapter82 - 접근 지정자(Access Modifier)
<details><summary>주요 내용
</summary>


## 접근 지정자(Access Modifier)
  
- 일부 요소에 접근 권한이라는 것을 지정할 수 있으며 이를 접근 지정자 또는 가시성 지정자라고 한다 
  
|이름|의미|
|---|---|
|public|모든 곳에서 접근 가능. 접근 지정자를 생략하면 기본적으로 public이 된다|
|internal|같은 모듈 안에서 접근 가능. 여기서 모듈은 IntelliJ 프로젝트의 모듈을 가리킨다|  
|protected|클래스 내부와, 서브클래스 안에서만 접근 가능하다| 
|private|프로퍼티와 멤버 함수일 경우, 해당 클래스 안에서만 접근 가능하고, 그 외의 경우, 같은 파일 내에서만 접근 가능하다|  
  
  
```kotlin
  
  class Rectangle(private val width: Int, private val height : Int)
{
    val area : Int
    get() = width * height
}



fun main(){
    val rect  = Rectangle(5,7)
    //println(rect.width) // private이기 때문에 error
    println(rect.area)
}
  
```  
  
  
  
  
  
  
  
  
</details>


---


# Chapter83 - 접근 지정자 : private
<details><summary>주요 내용
</summary>


## 접근 지정자 : private
  
- private로 선언한 변수는 해당 파일에서만 접근이 가능하다
 
  
```kotlin
  
  public class Person(age:Int){
    public var age = age
    private set // default Setter를 private로 선언한다 

    public val isYoung public get() = age<30 //Getter는 어디에서나 접근이 가능하다 
}
  
```  
  
  
</details>


---



# Chapter84 - 접근 지정자 : protected
<details><summary>주요 내용
</summary>


## 접근 지정자 : protected
  
- open된 상위클래스의 protected 프로퍼티는 상속을 받은 하위클래스에서 사용이 가능하다 
  

 ```kotlin
  
open class AAA(protected val number: Int)

class BBB(number: Int) : AAA(number)
{
    fun printNumber() = println(number) // 상속을 받았기 때문에 AAA의 프로퍼티에 접근 가능
}

fun main(){
    val test = BBB(36)
    test.printNumber()
}
  
 ``` 
  
  
</details>



---




# Chapter85 - 접근 지정자 오버라이딩
<details><summary>주요 내용
</summary>

## 접근 지정자 오버라이딩

- 오버라이딩을 통해 protected인 프로퍼티나 멤버 함수의 접근 지정자를 public으로 변경할 수 있다  
  
```kotlin
  
  open class A(protected open val number: Int)
{
    protected open fun hello(){
        println("hello")
    }
}

class B(number: Int) : A(number)
{
    public override val number : Int
    get() = super.number

    public override fun hello() = super.hello()
}

fun main(){
    val b = B(26)
    val a : A = b 
    
    // println(a.number) error 
    // a.hello()  error 
    
    println(b.number) // b에서 타입을 override 해줬기 때문에 접근이 가능
    b.hello()
}
  
```  
  
  
- private인 프로퍼티와 멤버 함수는 서브클래스에서도 접근이 불가능하기 때문에 **오버라이딩 할 수 없다**
 
- private인 프로퍼티와 멤버 함수에는 open 키워드 자체를 지정할 수 없
  
  
  
  
  
  
</details>



---





# Chapter86 - 확장 함수(Extension Function)
<details><summary>주요 내용
</summary>


## 확장 함수(Extension Function)
  
- 확장 함수 문법을 이용하여, 상속 없이 클래스 외부에서 멤버 함수를 추가할 수 있다  
  
- **리시버(Receiver) 타입** : 함수를 주입할 클래스 
  
- this를 사용하여 리시버 타입의 프로퍼티나 멤버 함수에 접근할 수 있다. 단, private나 protected인 멤버에는 접근할 수 없다 
  
  
  
```kotlin
  
  fun String.isNumber(): Boolean {
    var i = 0
    while(i < this.length)
    {
        if(!('0' <= this[i] && this[i]<='9'))
            return false
        i+=1
    }
    return true 
}



fun main(){
    println("1234567890".isNumber())
    println("500원".isNumber())
}
  
```  
  
  
  
</details>



---




# Chapter87 - 확장 프로퍼티(Extension Property)
<details><summary>주요 내용
</summary>


## 확장 프로퍼티(Extension Property)
  
- 확장 함수처럼 프로퍼티 이름 앞에 리시버 타입을 적는다 
  
```kotlin
  
  val String.isLarge : Boolean
    get() = this.length >= 10


fun main(){
    println("1234567890".isLarge)
    println("500원".isLarge)
}
  
```  
  
  
  
- 확장 프로퍼티에는 Field가 존재하지 않는다 
  
</details>



---




# Chapter88 - 객체 선언(Object Declaration), 싱글톤 
<details><summary>주요 내용
</summary>

### 객체 선언(Object Declaration)

```kotlin
  
object Person2
{
    var name : String = ""
    var age : Int = 0
    fun print(){
        println(name)
        println(age)
    }
}
fun main(){
    Person2.name = "Singleton"
    Person2.age = 45
    Person2.print()
}
  
```  
  
- **프로그램 전체에서 공유할 수 있는 하나뿐인 객체를 선언할 때** 사용한다  
 
- object 키워드 덕에 자바에서 작성해야만 했던 싱글톤 패턴 코드를 더 이상 쓰지 않아도 된다   
  
  
</details>





---





# Chapter89 - 동반자 객체(Companion Object)
<details><summary>주요 내용
</summary>

## 동반자 객체(Companion Object)
  
- 클래스 안에 포함되는 이름 없는 객체. **어떤 클래스의 모든 인스턴스가 공유하는 객체** 를 만들고 싶을 때 사용한다
  
```kotlin
  
  class Person3 private constructor(){
    companion object{
        fun create():Person3{
            countCreated +=1
            return Person3()
        }
        var countCreated = 0 // Person의 인스턴스를 집계하기 위한 프로퍼티 
        private set          // 외부에서 함부로 값을 조정하는 것을 방지하고자 private로 설정 
    }
}

fun main(){
    val a = Person3.create()
    val b = Person3.create()
    println(Person3.countCreated)
}
  
```  
  
- **companion object 키워드** 로 동반자 객체를 선언한다 
  
- 동반자 객체는 **자신이 속한 클래스의 이름으로 접근할 수 있다**
  
- 동반자 객체는 클래스당 한 개만 존재한다 
  
- 코틀린에는 static 키워드가 존재하지 않기 때문에, 자바에서의 static과 같은 효과를 얻고 싶으면 동반자 객체를 사용해야 한다 
  
- `객체이름.프로퍼티` 로 함수 호출 및 프로퍼티에 접근한다 
  
</details>


---




# Chapter90 - inline 함수
<details><summary>주요 내용
</summary>

## inline 함수

- inline 함수를 사용하면, 실행 흐름을 점프하지 않고 함수 호출문을 함수의 몸체로 대체하기 때문에 성능을 조금이나마 개선할 수 있다   
  
```kotlin
  
inline fun hello(){
    println("Hello")
    println("Kotlin")
}

fun main(){
    hello()
    hello()
    hello()
  """
    println("Hello")
    println("Kotlin")
    println("Hello")
    println("Kotlin")
    println("Hello")
    println("Kotlin")
  """
}
  
```  
  
- inline 함수는 함수 속의 문장을 재활용하지 않기 때문에, 문장이 많은 함수를 inline으로 바꾸면 프로그램의 크기가 기하급수적으로 늘어난다 
  
- inline 함수는 함수 몸체 코드가 무한대로 늘어날 수 있기 때문에 재귀호출이 불가능하다 
  
  
</details>


---




# Chapter91 - const
<details><summary>주요 내용
</summary>


## const
  
- val 변수 앞에 const 키워드를 붙이면 변수에 접근하는 코드를 변수에 저장된 값으로 대체시킨다 
 
- const가 붙은 변수에는 리터럴로 이루어진 표현식만 저장이 가능하다 
  
```kotlin
  
const val hello = "Hello" + "World"

object Foo
{
    const val bar = "bar"
}

fun main(){
    println(hello) // 컴파일 시 hello가 Hello World로 대체돼서 번역된다 
    println(Foo.bar)
    println(hello)
    println(Foo.bar)
}
  
```  
  
- const가 붙은 변수는 리터럴로 대체되기 때문에 **코틀린 문법 중 리터럴만 와야 하는 자리** 에 사용할 수 있다   
  
  
</details>

---


# Chapter92
<details><summary>주요 내용
</summary>



  
  
  
</details>

---


# Chapter93
<details><summary>주요 내용
</summary>



  
  
  
</details>

---


# Chapter94
<details><summary>주요 내용
</summary>



  
  
  
</details>




---


# Chapter95
<details><summary>주요 내용
</summary>



  
  
  
</details>





---


# Chapter96
<details><summary>주요 내용
</summary>



  
  
  
</details>





---


# Chapter97
<details><summary>주요 내용
</summary>



  
  
  
</details>





---


# Chapter98
<details><summary>주요 내용
</summary>



  
  
  
</details>



---


# Chapter99
<details><summary>주요 내용
</summary>



  
  
  
</details>



---


# Chapter100
<details><summary>주요 내용
</summary>



  
  
  
</details>



