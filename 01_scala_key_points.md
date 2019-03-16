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

