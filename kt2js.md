# Kotlin for Javascript DEVs... or vice versa

## what in common:

-   Modern Syntax
-   OOP + FP
-   Multiplatform

Variables & Constants

```javascript
//javascript

const TLDW = "too long, don't read";
let imCool = true;
imCool = false;
TLDW = "something else"; // error
```

```kotlin
//kotlin

val TLDW = "too long, don't read" // constant
var imCool = true
imCool = false
TLDW = "something else" // compile error
```

### Strings

```javascript
//javascript
const captain = "Steve Roger";
const ironMan = `
Tony Stark
is
Iron Man
`;
```

```kotlin
//kotlin

val captain ="Steve Roger"
val ironMan = """
Tony Stark
is
Iron Man
"""
```

### String templates

```javascript
//javascript
const cap = "Cap";
const iron = "Tony";
const thor = "Odin's Son";

const avengers = `Strongest Avengers: ${cap}, ${iron} and ${thor}`;
```

```kotlin
//kotlin

val cap = "Cap"
val iron = "Tony"
val thor = "Odin's Son"

val avengers = "Strongest Avengers: $cap, $iron and $thor"
```

### Function

```javascript
//javascript
function multiply(a, b = 1) {
	return a * b;
}
```

```kotlin
//kotlin

fun multiply(a:Int, b:Int =1): Int {
   return a*b
}

// or
fun multiply(a:Int, b:Int = 1) = a*b

//named parameters
fun format(from: String,
             formatStr:String = "%s",
             allCaps:Boolean = false
             ):String{
} //

```

### Lambda Expression

```javascript
//javascript
const sum = (a, b) => a + b; // sum(a,b) or sum.invoke(a,b)

const endGame = avengers.filter(hero => hero.survivedFromTheSnap);
const powers = users.map(user => user.power);
```

```kotlin
//kotlin


val sum : (Int, Int) -> Int = { x,y -> x+y } // same usage: sum(a,b) or sum.invoke(a,b)
//or
val sum = {x:Int, y:Int -> x+y}

val endGame = avengers.filter {hero -> hero.survivedFromTheSnap };
//or
val endGame = avengers.filter { it.survivedFromTheSnap };
val powers = users.map { it.power };

```

### Collections

-   map / filter / reduce / fold , etc.

### Flow controls:

```javascript
//javascript
if (number > 0) {
	console.log("Positive number");
} else {
	console.log("Negative number");
}

val getColor = (number) => number > 0 ? 'Red' : 'Green'
```

-   Kotlin

```kotlin
//kotlin

if (number > 0) {
    print("Positive number")
} else {
    print("Negative number")
}

val getColor = { number:Int =>  if (number > 0) "Red" else "Green" }
```

-   JS

```javascript
//javascript
switch (selectedFruit) {
	case "orange":
		console.log("Oranges are 59 cents a pound.");
		break;
	case "apple":
		console.log("Apples are 32 cents a pound.");
		break;
	case "cherry":
		console.log("Cherries are one dollar a pound.");
		break;
	case "mango":
	case "papaya":
		console.log("Mangoes and papayas are 3 dollars a pound.");
		break;
	default:
		console.log(`Sorry, we are out of ${selectedFruit}.`);
}
```

-   Kotlin

```kotlin
//kotlin

when(selectedFruit) {
    "orange" -> print("Oranges are 59 cents a pound.")
    "apple" -> print("Apples are 32 cents a pound.")
    "cherry" -> print("Cherries are one dollar a pound.")
    "mango", "papaya" -> print("Mangoes and papayas are 3 dollars a pound.")
    else -> print("Sorry, we are out of $selectedFruit.")
}
```

### Loop

```javascript
//javascript

const len = students.length;
const step = 2;
for (let i = 0; i < len; i += step) {
	// take action
}
//even better with
for (const student of students) {
	// or use forEach
	// take action
}
```

-   Kotlin

```kotlin
//kotlin

val len = students.size;
val s = 2
for(var i = 0; i < len; i +=s){
   // take action
}
// use ranges
for(var i  in 0..len-1 step s){}
// or
for(var i in 0 until len step s){}
// or
for(var i in len downTo 0 step s){}
//even better with
for(student in students){ // or use forEach
   // take action
}
```

### Destructuring Assignment

```javascript
//javascript
const coordinates = [5, 10, 15];
const [x, y, z] = coordinates;

const obj = {
   a:1,
   b:2,
   c:3
   d:4
}

const (x,y,z) = obj // x=1, y=2, z=3
```

-   Kotlin

```kotlin
//kotlin

val coordinates = arrayOf(5, 10, 15)
val (x, y, z) = coordinates

val triple = Triple<Int, Int,Int>(1,2,3)
val (first, second) = triple
```

### Class

```javascript
//javascript
class Monster {
	constructor(name, color, numEyes) {
		this.name = name;
		this.color = color;
		this.numEyes = numEyes;
	}
	speak(likes) {
		return `My name is ${this.name} and I like ${likes}`;
	}
}
var nhama = new Monster("Nhama", "red", 1);
nhama.speak("guacamole");
```

-   Kotlin

```kotlin
//kotlin

class Monster(val name: String, val color: String, val numEyes: Int) {
  fun speak(likes: String):String {
      return "My name is $name and I like $likes"
  }
}
var nhama = Monster("Nhama", "red", 1)
// Kotlin doesn't have a `new` keyword - you instantiate a class by calling it directly
nhama.speak("guacamole")
```

### Async

| language | type    | syntax                                     |
| -------- | ------- | ------------------------------------------ |
| JS       | Promise | async/await                                |
| Kt       | Defer   | suspend/await (pls check kotlin Coroutine) |
