# Key points
- overloading operators
	- All types even primitives are objects/classes in scala
	- All operators in scala are methods
```scala
1.+(1) //eq to 1+1
1 toString //postfix ops use -language:postfixOps to disable the warning in REPL
```

- We can ommit the () for methods do not require an argument
```scala
def isEven(n:Int) = (n % 2) == 0
List(1,2,3,4,5,6) filter isEven foreach println
```

- If statement in Scala
- **No Ternary expression in the Scala**
```scala
if (2+2==5){
	println("hello from 1984")
}
else if (2+2==3){
	println("hello from remedial math class?")
}
else
{
	println("Hello from Future!")
}
```

- For loop
	- for each element in a collection
```scala
val dogBreeds = List("Doberman", "Yorkshire Terrier", "Dachshund",
                     "Scottish Terrier", "Great Dane", "Portuguese Water Dog")

for (breed <- dogBreeds)
  println(breed)
```
	- iterates thru a range
```scala
for (i<- 1 to 10) println(i) // no curly braces here for only 1 statement inside the for loop
```
	- guard for extra filtering
```scala
val dogBreeds = List("Doberman", "Yorkshire Terrier", "Dachshund",
                     "Scottish Terrier", "Great Dane", "Portuguese Water Dog")
for (breed <- dogBreeds if breed.contains("Terrier")) //add guard inside the for expression
  println(breed)
```
- Yielding
```scala
val dogBreeds = List("Doberman", "Yorkshire Terrier", "Dachshund",
                     "Scottish Terrier", "Great Dane", "Portuguese Water Dog")
val filterdBreeds = for (breed <- dogBreeds if breed.contains("Terrier")) 
  yield breed // yield
```

- Extracting options and pattern matching in the for loop
```scala
val dogBreeds = List(Some("Doberman"), None, Some("Yorkshire Terrier"), 
                     Some("Dachshund"), None, Some("Scottish Terrier"),
                     None, Some("Great Dane"), Some("Portuguese Water Dog"))
println("first pass:")
for {
  breedOption <- dogBreeds
  breed <- breedOption
  upcasedBreed = breed.toUpperCase()
} println(upcasedBreed)

println("second pass:")
for {
  Some(breed) <- dogBreeds
  upcasedBreed = breed.toUpperCase()
} println(upcasedBreed)

```
- Scala operators
	- & and | are non-short-circuiting operators 
	- && and || are short-circuiting operators
```scala

== //scala use == as using .equals and uses eq as using == in java

```

- Try-catch-final in scala
	- file lines counter
```bash
scalac TryCatch.scala
```
- 

- Lazy eval
```scala
object ExpensiveResource {
  lazy val resource: Int = init()  
  def init(): Int = { 
    // do something expensive
    0
  }
}
```

- Enumeration
```scala
object Breed extends Enumeration {
  type Breed = Value
  val doberman = Value("Doberman Pinscher")
  val yorkie   = Value("Yorkshire Terrier")
  val scottie  = Value("Scottish Terrier")
  val dane     = Value("Great Dane")
  val portie   = Value("Portuguese Water Dog")
}
import Breed._

// print a list of breeds and their IDs
println("ID\tBreed")
for (breed <- Breed.values) println(s"${breed.id}\t$breed")

// print a list of Terrier breeds
println("\nJust Terriers:")
Breed.values filter (_.toString.endsWith("Terrier")) foreach println
// anonymous funcition
Breed.values filter (i=>i.toString.endsWith("Terrier")) foreach println

def isTerrier(b: Breed) = b.toString.endsWith("Terrier")
println("\nTerriers Again??")
Breed.values filter isTerrier foreach println
```
