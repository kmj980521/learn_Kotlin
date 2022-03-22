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


# Chapter92 - lateinit
<details><summary>주요 내용
</summary>


## lateinit
  
- **lateinit 키워드** 가 붙은 프로퍼티는 클래스 안에서 바로 초기화하지 않아도 된다 

- **lateinit 키워드는 var 키워드에서만 가능하다**
  
```kotlin
  
  class Rect{
    lateinit var pt:Point
    lateinit var pt2:Point

    val width: Int get() = pt2.x - pt.x
    val height: Int get() = pt2.y - pt.y
    val area get() = width * height
}

fun main(){
    val rect = Rect()
    rect.pt = Point(3,3)
    rect.pt2 = Point(6,5)

    println("너비: ${rect.width}")
    println("높이: ${rect.height}")
    println("넓이:${rect.area}")
}
  
```  
  
- lateinit 프로퍼티가 초기화되었는지 여부를 확인하는 방법  
  
```kotlin
  if(rect::pt.isInitialized) {}
```  
  
</details>

---


# Chapter93 - Nullable 리시버
<details><summary>주요 내용
</summary>


## Nullable 리시버
  
```kotlin
  
fun String?.isNumber(){ // 리시버 타입에 ?가 붙어 있고 이것이 Nullable 리시버 
    if(this==null)
        println("문자열이 null입니다")
}

fun main(){
    val empty : String ? = null
    empty.isNumber() 
}
  
```  
  
- 확장 함수의 리시버 타입이 Nullable이기 때문에, 표현식의 값이 null이어도 확장 함수를 호출할 수 있다   
  
</details>

---


# Chapter94 - 동반자 객체의 확장 함수
<details><summary>주요 내용
</summary>

## 동반자 객체의 확장 함수 

```kotlin
  
 fun 클래스 이름.Companion.함수 이름()
  
```  
  
- 동반자 객체는 클래스 이름만으로 접근할 수 있지만, 확장 함수를 선언할 때 그렇게 하면 동반자 객체가 아닌 클래스 자체에 멤버 함수가 추가되므로 식별자를 반드시 적어준다 
  
```kotlin
  
class Person { companion object}
fun Person.Companion.create() = Person

fun main() = Person.create()
  
```  
  
  
</details>




---


# Chapter95 - 확장 함수의 리시버 타입이 상속 관계에 있을 때
<details><summary>주요 내용
</summary>


## 확장 함수의 리시버 타입이 상속 관계에 있을 때
  
- 확장 함수는 멤버 함수와는 다르게 **참조 변수가 실제로 가리키는 객체의 타입을 따르지 않고, 참조 변수의 타입을 그대로 따른다**  
  
</details>





---


# Chapter96 - 추상 클래스(Abstract Class)
<details><summary>주요 내용
</summary>


## 추상 클래스(Abstract Class)
  
- 공통되는 멤버를 전파하는 용도로 쓴다   
  
  
- 클래스를 추상 클래스로 만드려면, 클래스 선언 맨 앞에 **abstract 키워드** 를 붙인다

- 추상 클래스는 일부 멤버의 내용이 비어있는 불완전한 클래스이기 때문에 객체를 생성할 수 없다 
  
- abstract 키워드는 그 자체로 **open 키워드를 포함하고 있다**
  
</details>





---


# Chapter97 - 인터페이스(Interface)
<details><summary>주요 내용
</summary>


## 인터페이스(Interface)
  
- 클래스에 어떤 멤버 함수와 프로퍼티가 **반드시 존재한다는 것을 보장하기 위한 장치**  
  
  
```kotlin
  
interface Printalbe{
    fun print():Unit
}

class A1 : Printalbe
{
    override fun print() {
        println("Hello A")
    }
}
fun print(anything:Printalbe)
{
    anything.print()
}



fun main(args:Array<String>){
    print(A1())
}
  
```  
  
- 인터페이스는 멤버 함수, 추상 멤버 함수, 추상 프로퍼티를 가질 수 있고, **일반 프로퍼티와 생성자는 가질 수 없다**
  
- 인터페이스 안의 멤버 함수는 내용이 비어있으면 자동으로 abstract가 붙는다 
  
- 인터페이스는 생성자가 존재하지 않기 때문에 **상속할 때 이름 옆에 ()를 쓰지 않는다** 
  
- 인터페이스 안에 있는 추상 멤버 함수는 모두 구현을 해야 한다 
  
- 인터페이스는 어떤 클래스에 플러그인을 추가한다는 개념에 가깝다 
  
  
</details>





---


# Chapter98 - 다이아몬드 문제(The Diamond Problem)
<details><summary>주요 내용
</summary>

## 다이아몬드 문제(The Diamond Problem)
  
  
  
</details>



---


# Chapter99 - 중첩 클래스(Nested Class)
<details><summary>주요 내용
</summary>


## 중첩 클래스(Nested Class)
 
- 클래스 안에 또 다른 클래스 
  
```kotlin
  
class Outer
{
    private val property:Int = 16
    class Nested{
        fun hello() = println("중첩된 클래스")
        //println(property) // error
    }
}
fun main(args:Array<String>)
{
    val instance : Outer.Nested = Outer.Nested()
    instance.hello()
}
  
```  

- 내부에 있는 클래스는 실제로는 완전히 분리된 장소에 있다 
  
- Outer의 인스턴스와 Outer.Nested의 인스턴스는 서로 어떠한 프로퍼티나 멤버 함수도 공유하지 않는다 
  
</details>



---


# Chapter100
<details><summary>주요 내용
</summary>


## 내부 클래스(Inner Class)
  
- 인스턴스가 바깥 클래스의 **인스턴스에 완전히 소속된다** 
  
- **inner 키워드** 를 붙인다 
  
```kotlin
  
class Outer2(private val value:Int)
{
    fun print(){
        println(this.value)
    }

    inner class Inner(private val innerValue:Int)
    {
        fun print(){
            this@Outer2.print()
            println(this.innerValue + this@Outer2.value)
        }
    }
}
fun main(args:Array<String>)
{
    val instance : Outer2 = Outer2(610)
    val innerInstance: Outer2.Inner = instance.Inner(40)
    innerInstance.print()
}
  
```  
  
- 내부 클래스의 인스턴스를 생성하려면 반드시 **바깐 클래스부터 인스턴스를 생성** 하고 ** 참조 변수.생성자()** 를 해야 한다 
  
- **해당 코드에서는 this@Outer2 이다** 
  
- ** this@Outer 키워드** 를 이용하여 자신이 속한 바깐 클래스의 인스턴스에 접근할 수 있다 
  
  
  
  
</details>



