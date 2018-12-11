# _Discovery and analysis of Kotlin_

- _Yudi Tao_ 
- _yudi.tao@uoit.net_

## About the language

_Kotlin is a programming language that bulids base on __Java__ and run on __Java Virtual machine__. It using a similar syntax with __Java___

- Kotlin was first be invented by __JetBrains__ in 2011, which is aiming at Android developing and website programming. In 2017 Google has announced their first-class supprot language on Android is Kotlin  
- There is one thing that is interesting, Kotlin could also be interpt as a __script__, a file name end with extention __.kts __could be directly interpt by its complier. With simple language syntax, Kotlin could be easily getting start with. Another thing that is interesting is that Kotlin can preform __operator overloading__ in a similar way as C++.


## syntax

### print statement

Simply using __``print()``__ and __``println()``__

```
println("Hello ")
print("world")
```
### declare variable in a particular type

Use the key word __```var```__

```
var a:Double
a=5.0 
```
### const value
```
val PI = 3.14
```
__variable can be implied declare by value__
```
var b = 1.0
```
### type casting

Using __`a.toInt()`__ means convert __`a`__ into a Integer 

```
var c = a.toInt()

var d:Int = b.toInt()
```
### Any type

There exist a type of value simply called __``Any``__ means any one of types could be decare 

```
var some:Any = 1.0
```
### type check

Similar with Python key word __``is``__, Kotlin have the similar usage. 

```
println(some is Int)
```
### arbitrary expression in template

Present by __``$``__ sign in string.

```
println("Max of $a and $b: " + maxOf(a,b))
```
### arbitrary expression using function

Function can also be arbitrary using __``${}``__.
```
println("Does $some is a Double? ${some is Double}")
println("describe $a: ${describe(a)}")
println("describe $b: ${describe(d)}")
println("describe 10: ${describe(10)}")
```

### function can be define in function
```
fun main(){
    var x = 0
    fun incrementX() {
        x += 1
    }
    incrementX()
}
```
- space that outside quote will not affect the program running
```
println("X is       now: "         +     x     +" and here is $PI"     )
```

### single type list

Kotlin does not have keyword __<s>new</s>__.

Creating a list, Array, would just use __``listOf<type>() arrayOf<type>() ``__

```
var list = listOf<Int>(1,2,4,6)
```
### mix type list

List can be creating multiple different types.

```
var list2 = listOf("abc",1,"14",2.5)
```

### loop

- for loop iteration in range 1 - 10: __``1..10``__
```
for (i in 1..10){
    print("$i ")
}
```
- foreach 
```
for (l in list){
    print("$l ")
}
```

- size of a list
```
list.size
```
-  indexing
```
print("${list2[i]} ")
```

-  inc 
```       
i++
```
- while loop 
```
var i=0
while (i<list.size){
print("${list2[i]} ")
i++
}
```

### check if contains

Using kerword __``in``__

```
println("\nprint directly: $list")
println("does 12 contain in $list? ${12 in list}")
```
### class delceration

- __`open`__: explicit modifiers for overridable members

- __`Shapes(name:String)`__: the main default constructor of a Class 

```
open class Shapes(name:String){
    public var name:String="Shape"
    private var edges:Int = 0
    protected var id:Int=0
    }
```
- Class initializer 
```
    init {
        println("Initialize a shape.")
    }
```
- Inheritance 
    - circle(name:String,radius:Double): __`Shapes(name)`__ 
    means inherit from super class and override the default constructor
```
//pow function was not in base of Kotlin
import Kotlin.math.pow

class circle(name:String,radius:Double):Shapes(name){
    private var radius:Double=0.0;
    init {
        this.name=name;
        this.radius=radius;
        println("Initialized: $name")
    }
    public fun Area():Double{
        //power of 2 times PI
        return radius.pow(2)*3.14
    }
}
```
- To create a instance:
    - __var__ ``foo:[Type] = constructor()``
    - ``foo.fun(), foo.a`` to call class member function and variable
    ```
    var cir:Circle = Circle("circle",2.5)
    println("${cir.name}'s Area: ${cir.Area()}")
    ```

### packages

- import a package with __``as``__
```
import Polite.introduction as polite
import Rude.introduction as rude
```
- to use packages
```
polite("Tom")
rude("Jude")
```
### Input

- use !! for Null-safe input i.e. non-null assertion
```
var input = readLine()!!
println("Your input: $input")
```
- try block
```
var word ="Word"
try {
    word.toInt()
}catch (e: NumberFormatException){
    //Java packages still work in Kotlin, since Kotlin is bulit on Java
    //such as System.out and System.err 
   System.err.println("Unsupported Type casting.")
   }
```
## About the tools
__Kotlinc:__
```
$ kotlinc hello.kt -include-runtime -d hello.jar
```
__Kotlin:__

Complie __.kt__ file into __.jar__ file. 

```
$ kotlin -classpath hello.jar HelloKt
```
- __or__

```
$ java -jar hello.jar
```

## About the standard library

### List

```
var list = listOf(1,2,13,4,15,16,62,6,37,1)
```

- list could be directly print by __``print()``__ and __``println()``__ 
    
#### indexing

```
list[1]
```

#### sorting 

```
list.sorted()
```
    
### Array

```
var array = arrayOf(1,2,34,2,5,25,25,26,4)
```

- Array cannot be <s>indexing</s> and <s>print</s>,however it could transform to list by `array.toList()`
    
#### sort
    
```
array.sorted()
```
### ArrayList

```
 var arrayList:ArrayList<Int> = arrayListOf(1,23,1,1,5,16,19,12,41,30,10)
```

#### Add into ArrayList
    
- append

```
arrayList.add(13)
```
        
- add by indexing

```
arrayList.add(4,10)
```

- ArrayList could be directly print by __``print()``__ and __``println()``__ 

#### indexing

```
arrayList[1]
```

#### sorting

```
arrayList.sorted()
```

### HashMap

```
var map = mutableMapOf<String,Int>()
```

#### add into Mutable Map 
    
    ```
    map.put("one",1)
    map.put("three",3)
    map.put("five",5)
    map.put("two",2)
    map.put("four",4)
    ``` 
- mutableMap could be directly print by __``print()``__ and __``println()``__ 
    
#### get value by key

```
map.get("two")
```
    
#### sorting
- normal sort on map (Sort by Key)

```
map.toSortedMap()
```
- sort by values (Sort by Value)

```
map.toList().sortedBy{(key,value)->value }.toMap()
```
        
### File I/O
Kotlin can directly use __java.io__ for File I/O

#### Read File
- For Each Line
```
fun readForEachLine(fileName: String)
        = File(fileName).forEachLine{println(it)}
```
 - __`it`__ is the keyword as parameter that passing into a lamda function
- Read By Buffered Reader
```
fun readByBufferedReader(fileName: String): List<String>
        = File(fileName).bufferedReader().readLines()
```
- Read Lines
```     
fun readByReadLines(fileName: String): List<String>
        = File(fileName).readLines()
```
#### Write File

- Write Text
```
File("Write.txt").writeText("1")
```
- Append Text
```
File("Write.txt").appendText("Append one line.")
```
- Print Writer
```
File("Write.txt").printWriter().use{ 
    out -> out.println("2") 
    }
```
- Buffered Writer
```
File("Write.txt").bufferedWriter().use { 
    out -> out.write("3") 
    }
```

    
## About open source library

> _Describe at least one contribution by the open source
community written in the language._

## Analysis of the language

> _Organize your report according to the project description
document_.


