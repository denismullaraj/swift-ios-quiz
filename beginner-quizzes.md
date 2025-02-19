## Swift Beginner

This quiz test your knowledge of Swift programming and fundamentals. 

## Table of Contents
- [Swift Basics](#swift-basics)
- [Collections](#collections)
- [Functions & Closures](#functions--closures)
- [Classes & Structs](#classes--structs)
- [Optionals](#optionals)
- [Enumerations](#enumerations)

## Swift Basics

### 1. How many bits are allocated to an `Int`?
- [ ] A) 8-bit.
- [ ] B) 16-bit.
- [ ] C) 32-bit.
- [ ] D) Depends on the device.
- [ ] E) Unlimited.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  D) Depends on the device. ✅ 

- **Explanation:**  
  Swift's integers are 32-bit on 32-bit devices (iPhone 5 and earlier) and 64-bit on 64-bit devices (iPhone 5S and later).
</details>

---

### 2. Range usage - What will output when you run it?
```swift
for countDown in 5...0 {
    print(countDown)
}
```

- [ ] A) 5, 4, 3, 2, 1.
- [ ] B) 1, 2, 3, 4, 5.
- [ ] C) 0, 1, 2, 3, 4, 5.
- [ ] D) 15, 4, 3, 2, 1, 0.
- [ ] E) Nothing will be output.
- [ ] F) This code will not compile.
- [ ] G) This code will compile but crash.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  G) This code will compile but crash. ✅ 

- **Explanation:**  
  The code will compile succesfully, but crash at runtime: Swift doesn't allow to generate ranges where the start value is greater than the end value.
</details>

---

### 3. String concatenation - What will output when you run it?
```swift
let apples = "0"
let oranges = "5"
let basket = apples + oranges
print(basket)
```

- [ ] A) 5.
- [ ] B) "5".
- [ ] C) "05".
- [ ] D) "50".
- [ ] E) This code will compile but crashes.
- [ ] F) This code is not allowed.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  C) "05". ✅ 

- **Explanation:**  
  Swift Strings can be joined together using the + operator. If you expected them to sum as numbers, you had to cast them to Int and sum them.
</details>

---

### 4. What data type does `pi` have in the code below?
```swift
let pi = 3.14
```

- [ ] A) Decimal.
- [ ] B) Float.
- [ ] C) Int.
- [ ] D) Double.
- [ ] E) This code will not compile.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  D) Double. ✅ 

- **Explanation:**  
  Swift will use the `Double` data type when giving a floating-point number.
</details>

---

### 5. Check the code below and tick the best affirmation.
```swift
let cat = "🐱"; print(cat)
```

- [ ] A) Swift doesn't require semicolon, so you can omit it.
- [ ] B) The semicolon is used to separate emojis.
- [ ] C) Writing multiple statements in a single line requires a semicolon.
- [ ] D) It will work both with a semicolon and without it.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  C) Writing multiple statements in a single line requires a semicolon. ✅ 

- **Explanation:**  
  Semicolons aren't required in Swift, but you can also use them after each statement in your code. They are required if you want to write multiple separate statements on a single line.
</details>

---

### 6. Strings - What will be the output and value of `welcome` after code is executed?
```swift
var welcome = "hello"
let range = welcome.index(welcome.endIndex, offsetBy: -4)..‹welcome.endIndex welcome.removeSubrange(range)
print(welcome)
```

- [ ] A) "lo".
- [ ] B) "o".
- [ ] C) 1111.
- [ ] D) "h".
- [ ] E) "he".
- [ ] F) Code compiles fine but will crash during execution.
- [ ] G) "hello".

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  D) "h". ✅ 

- **Explanation:**  
  To remove a substring at a specified range, we use the `removeSubrange(_:)` method. We are removing a substring from the last character going backward of 4 chars, "ello"  is being removed. Result is "h".
</details>

---

### 7. Strings - What will output when you run it?
```swift
var thought = "Dogs are cool"
thought.replacingOccurrences(of: "Dogs", with: "Cats")
print(thought)
```

- [ ] A) "Cats are Dogs".
- [ ] B) "DogsCats are cool".
- [ ] C) "Cats are cool".
- [ ] D) Code compiles fine but will crash during execution.
- [ ] E) "Dogs are cool".

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  E) "Dogs are cool". ✅ 

- **Explanation:**  
  `replacingOccurrences(of:with:)` returns a new string in which all occurrences are replaced. The original string, `thought`, remains unchanged.
</details>

---

### 8. What will output when you run it?
```swift
let i = 1
if i {
    print("i is 1!")
}
```

- [ ] A) "i is 1!".
- [ ] B) 1.
- [ ] C) True.
- [ ] D) Code will not compile.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  D) Code will not compile. ✅ 

- **Explanation:**  
  Code will not compile because i is not a Boolean value but an Int, so it can't be compared like that. We could have compare it as `if i == 1 { .. }`.
</details>

---

### 9. How would you define Swift Language?

- [ ] A) Statically typed language.
- [ ] B) Dynamically typed language.
- [ ] C) None of them.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  A) Statically typed language. ✅ 

- **Explanation:**  
  Swift is a Static Type Language, meaning that types are checked before run-time. Try to write `var number = 5 + "hello"` and it won't compile. Meaning the type check happens at compile time, providing strong protections against an entire category of bugs.
</details>

[🔼 Back to Top](#table-of-contents)

---

## Collections

### 10. When we execute this code what will be the value of the array `weekdays`?
```swift
let weekdays = ["monday", "tuesday"]
weekdays.append("wednesday")
```

- [ ] A) ["wednesday"].
- [ ] B) ["monday", "wednesday"].
- [ ] C) ["monday", "tuesday", "wednesday"].
- [ ] D) ["monday", "tuesday"].
- [ ] E) This code will compile but crash.
- [ ] F) This code will not compile.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  F) This code will not compile. ✅ 

- **Explanation:**  
  This code will not compile because it modifies `weekdays` which is a `let`. To do it, you must use `var` keyword: `var weekdays = ["monday"...]`.
</details>

---

### 11. Array - What will output when you run it?
```swift
let chars = ["a", "b", "c"]
for char in chars[1...] {
    print(char)
}
```

- [ ] A) Code will not compile.
- [ ] B) Code will compile but it will crash when run.
- [ ] C) Code will run fine but output nothing.
- [ ] D) A special import is required.
- [ ] E) "a", "b", "c".
- [ ] F) "b".
- [ ] G) "b", "c".

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  G) "b", "c". ✅ 

- **Explanation:**  
  This range is called `one-sided range` and it continue as far as possible in one direction. Here for example the range includes from index 1 to the end of the `array`.
</details>

---

### 12. Dictionary - What will output when you run it?
```swift
var welcome = "hello"
let range = welcome.index(welcome.endIndex, offsetBy: -4)..‹welcome.endIndex welcome.removeSubrange(range)
print(welcome)
```

- [ ] A) ["YYZ": "Toronto Pearson"].
- [ ] B) ["YYZ": "Toronto Pearson", "DUB": """].
- [ ] C) ["YYZ": "Toronto Pearson", "DUB": nill].
- [ ] D) ["'YZ": "Toronto Pearson", "DUB":].

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  A) ["YYZ": "Toronto Pearson"]. ✅ 

- **Explanation:**  
  `removeValue(forKey:)` method removes the key-value pair if it exists and as well returns the removed value, or returns nil if no value existed.
</details>

---

### 13. What do we need to put into `airportCodes` to make it print the codes as commented within an array of String?
```swift
var welcome = "hello"
let range = welcome.index(welcome.endIndex, offsetBy: -4)..‹welcome.endIndex welcome.removeSubrange(range)
print(welcome)
```

- [ ] A) let airportCodes = \[String](airports.allKeys).
- [ ] B) let airportCodes = \[String](airports.keys).
- [ ] C) let airportCodes = \[String](airports.eachKey).
- [ ] D) let airportCodes = [airports.keys].
- [ ] E) let airportCodes = airports.keys.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  B) let airportCodes = \[String](airports.keys). ✅ 

- **Explanation:**  
  `airports.keys` returns the dictionary `keys`. To make out an array from those keys you simply typecasts it to [String]. So `let airportCodes = \[String](airports.keys)` is the correct answer.
</details>

---

### 14. What will be the value of newOnes after code is executed?
```swift
var ones = [1,1, 1,1,11
var newones = ones.reduce(0, +)
print(newOnes)
```

- [ ] A) [0,0,0,0,0].
- [ ] B) [0,1,2,3,4].
- [ ] C) 4.
- [ ] D) 5.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  D) 5. ✅ 

- **Explanation:**  
  `reduce(_:_:)` returns the result of combining the elements of the sequence using the given closure. In our case starting from 0, it sums (+) each value in the array. So 0+1+1+1+1+1 = 5.
</details>

---

### 15. What will be the value of `berries` after code execution?
```swift
let berries = [String]()
berries.append("Blueberry")
berries.append("Strawberry")
berries.append("Raspberry")
```

- [ ] A) ["Blueberry" "Strawberry", "Raspberry"].
- [ ] B) [].
- [ ] C) Code will not compile.
- [ ] D) Code will compile but crash.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  C) Code will not compile. ✅ 

- **Explanation:**  
  Code will not compile saying that `berries` is a `let` (constant) and can't be changed. To append new values and change it, you must declare it with `var` keyword, ex: `var berries = ...`.
</details>

---

### 16. What will be the output after this for loop?
```swift
let names = ["Anna", "Alex", "Brian"]
let count = names.count
for i in 0..<count {
    print("\(i + 1).\(names[i])")
}
```
- [ ] A) "O.Anna".
- [ ] B) "1.Anna", "2.Alex", "3.Brian".
- [ ] C) "O.Anna", "1.Alex", "2.Brian".
- [ ] D) "1.Anna", "2.Alex".
- [ ] E) The code compiles but will crash.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  B) "1.Anna", "2.Alex", "3.Brian". ✅ 

- **Explanation:**  
  Note that the array contains three items, but 0..<count only counts as far as 2 (the index of the last item in the array), because it’s a half-open range (which does not include the last range).
</details>

[🔼 Back to Top](#table-of-contents)

---

## Functions & Closures

### 17. Loops - What will output when you run it?
```swift
var quarantineDays = 1
repeat {
    quarantineDays = quarantineDays * 2
} while quarantineDays < 40
print(quarantineDays)
```

- [ ] A) 40.
- [ ] B) 32.
- [ ] C) 1.
- [ ] D) 64.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  D) 64. ✅ 

- **Explanation:**  
  `repeat-while` loop performs a single pass through the loop block first, before considering the loop’s condition, before 64, it was 32 and that was valid. It became 64 and exit the loop.
</details>

---

### 18. Loops - What will output when you run it?
```swift
var quarantineDays = 1
do {
    print(quarantineDays)
    quarantineDays = quarantineDays * 2
} while quarantineDays <= 40
```

- [ ] A) 1,2,4,8,16,32.
- [ ] B) 1,2,4,8,16,32,64.
- [ ] C) 1,2,4,8,16,32,40.
- [ ] D) The code will not compile.
- [ ] E) The code will compile but crash.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  D) The code will not compile. ✅ 

- **Explanation:**  
  In Swift the analogous to a `do-while` loop is the `repeat-while` loop, so the code will not compile as it is now.
</details>

---

### 19. Read the code from top to bottom, in which line there is an error?
```swift
import Foundation

func testHeightInCM(height: Int) -> String {
    message: String = "\(height)cm, "
    if height < 180 {
        message += "you are not that tall."
    } else {
        message += "wow, you are really tall!"
    }
    return message
}
print(testHeightInCM(height: 230))
```

- [ ] A) Line 4.
- [ ] B) Line 12.
- [ ] C) Line 10.
- [ ] D) There are no errors.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  A) Line 4. ✅ 

- **Explanation:**  
  `message` has never been declared, that means code will not compile. To successfully compile and run the code Line 4 needs to start with `var` keywords, ex: `var message: String = "..."`.
</details>

---

### 20. What is the value of `a` after the below code execution?
```swift
var a = 5
func changeValue(_ a: inout Int) {
    a = a + 5
}
changeValue(&a)
print(a)
```

- [ ] A) 5.
- [ ] B) 10.
- [ ] C) 15.
- [ ] D) Code will not compile.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  B) 10. ✅ 

- **Explanation:**  
  An `in-out parameter` has a value that is passed in to the function, is modified by the function, and is passed back out of the function to replace the original value.
</details>

[🔼 Back to Top](#table-of-contents)

---

## Classes & Structs

### 21. Classes - What will output when you run it?
```swift
class Person {
    var name: String 
    var secrets: String
}
let eva = Person(name: "Eva", secrets: "Love books")
print(eva.secrets)
```

- [ ] A) nil.
- [ ] B) "Love books".
- [ ] C) "Eva".
- [ ] D) Nothing will be output.
- [ ] E) This code will compile but crash.
- [ ] F) This code will not compile.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  F) This code will not compile. ✅ 

- **Explanation:**  
  Classes do not have member initialization by default as Structs do. The code will fail to compile because the `Person` class has no initializers.
</details>

---

### 22. Classes - What will output when you run it?
```swift
final class Bird {
    func chirp() {
        print("tsiu tsiu")
    }
}

class Crow: Bird {
    override func chirp) {
        print("caw caw!")
    }
}

let derry = Crow()
derry.chirp()
```

- [ ] A) "tsiu tsiu".
- [ ] B) "caw caw!".
- [ ] C) "caw caw!", "tsiu tsiu".
- [ ] D) The code will compile but crash.
- [ ] E) This code will not compile.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  E) This code will not compile. ✅ 

- **Explanation:**  
  The code tries to create a new class `Crow` that inherits from an existing `Bird` class. In this particular case, `Bird` class has been marked as `final`, which means it cannot be inherited from.
</details>

---

### 23. Are those two variables from the same class instance, are they identical?
```swift
class Person {
    var name: String?
}

let person = Person()
let samePerson = person
print(person == samePerson)
```

- [ ] A) True.
- [ ] B) False.
- [ ] C) Code will not compile.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  C) Code will not compile. ✅ 

- **Explanation:**  
  We are trying to asses they are identical (===), not equal (==), so the variables refer to the same class instance (Person). Code will run fine with `===`. To define equality, extra work is needed.
</details>

---

### 24. What will be the output for the two levels below?
```swift
class Level {
    var difficulty: Int = 1
}

var level1 = Level()
var level2 = level1
level2.difficulty = 2

print(level1.difficulty)
print(level2.difficulty)
```
- [ ] A) 1,2.
- [ ] B) 2,1.
- [ ] C) 2,2.
- [ ] D) 1,1.
- [ ] E) Code doesn't compile.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  C) 2,2. ✅ 

- **Explanation:**  
  Classes in Swift are reference types, a change in tutorial2 is also reflected in tutorial1. If we want just to `copy` tutorial1 and change difficulty only for tutorial2, Tutorial needs to be a Struct.
</details>

[🔼 Back to Top](#table-of-contents)

---

## Optionals

### 25. What will output when you run it?
```swift
let notes = ["Do", "Re", "Mi", "Fa"]
if let first = notes.first {
    print(first)
}
```

- [ ] A) "Re".
- [ ] B) Optional("Do").
- [ ] C) Optional("Fa").
- [ ] D) nil.
- [ ] E) "Do".
- [ ] F) Nothing will output.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  E) "Do". ✅ 

- **Explanation:**  
  Using `notes.first` will return an optional string (String?), but the `if let` unwraps it safely and hence the correct answer is "Do".
</details>

---

### 26. What is the value of the `output` String when this code is executed?
```swift
import Foundation
let hello = "Hello world!"
let output = NSString(hello)
```

- [ ] A) nil.
- [ ] B) "hello".
- [ ] C) "Hello world!".
- [ ] D) This code will not compile.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  E) This code will not compile. ✅ 

- **Explanation:**  
  Typecasting a `String` into an `NSString` is posible through the `NSString(string:)` initializer, which requires the `String` label in the initializer. let output = `NSString(string: stayHome)`.
</details>

---

### 27. What will output when you run it?
```swift
let greetings = ["Hi", "Hello", "Hey"]
for greeting in greetings {
    greeting = "\(greeting)!"
    print(greeting)
}
```

- [ ] A) "Hi", "Hello", "Hey".
- [ ] B) "Hi!", "Hello!".
- [ ] C) "Hi!", "Hello!", "Hey!".
- [ ] D) The code will not compile.
- [ ] E) The code will compile but crash.
- [ ] F) Nothing will be output.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  D) The code will not compile. ✅ 

- **Explanation:**  
  The code will not compile because it tries to modify `greeting` inside the loop. To correctly accomplisht this, `var` keywords must be used. `for var greeting in greetings {...}`.
</details>

---

### 28. What will output when you run it?
```swift
let greetings = ["Hi", "Hello", "Hey"]
let hi = greetings.first
let hiUp = hi.uppercased()
print(hiUp)
```

- [ ] A) nil.
- [ ] B) "HI".
- [ ] C) "HELLO".
- [ ] D) Optional("Hi").
- [ ] E) Optional("HI").
- [ ] F) The code will not compile.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  F) The code will not compile. ✅ 

- **Explanation:**  
  The code will not compile. `uppercased()` can only be called on `String` and not `String?`. In our `case greetings.first` return an `Optional` String. We could have used `hi?.uppercased()` as an example.
</details>

[🔼 Back to Top](#table-of-contents)

---

## Enumerations

### 29. What will output when you run it?
```swift
enum Beverage: String, CaseIterable {
    case coffee = "cof"
    case tea = "tea"
    case juice = "jui"
}

for beverage in Beverage.allCases {
    print(beverage)   
}
```

- [ ] A) "coffee", "tea", "juice".
- [ ] B) "cof", "tea", "jui".
- [ ] C) "coffee=cof", "tea=tea", "juice=jui".
- [ ] D) The code will not compile.
- [ ] E) The code will compile but crash.
- [ ] F) Nothing will be printed out.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  A) "coffee", "tea", "juice". ✅ 

- **Explanation:**  
  We can iterate over `allCases` and the code will compile and run fine. We are printing out the cases here, to print out their rawValue ("cof"..) we would have done `print(beverage.rawValue)`.
</details>

---

### 30. What will output when you run it?
```swift
enum Flower: String, CaseIterable {
    case rose
    case sunflower
    case tulip
}

for flower in Flower.allCases {
    print(flower.rawValue)   
}
```

- [ ] A) ",,".
- [ ] B) "".
- [ ] C) nil, nil, nil.
- [ ] D) "rose", "sunflower", "tulip".
- [ ] E) The code compiles fine but will crash.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  D) "rose", "sunflower", "tulip". ✅ 

- **Explanation:**  
  When `String` is used for raw values, the implicit value for each case is the text of that case’s name.
</details>

[🔼 Back to Top](#table-of-contents)

---