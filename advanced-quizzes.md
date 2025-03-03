# Swift Advanced Quiz

This quiz tests your knowledge of advanced Swift programming concepts and language features.

## Table of Contents
- [Swift Structures](#swift-structures)
- [Enumerations](#enumerations)
- [Control Flow](#control-flow)
- [Closures & Functions](#closures--functions)
- [Property Wrappers](#property-wrappers)
- [Type Extensions](#type-extensions)
- [Optionals & Collection Types](#optionals--collection-types)
- [Static & Lazy Properties](#static--lazy-properties)

## Swift Structures

### 1. What will output when you run it?
```swift
struct Game {
  var level: String
}
extension Game {
  init() {
    level = "Medium"
  }
}
let game = Game(level: "Easy")
print(game.level)
```
- [ ] A) Medium.
- [ ] B) Easy.
- [ ] C) Code does not compile.
- [ ] D) Code compiles fine but will crash.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  B) Easy. ✅ 

- **Explanation:**  
  The empty initializer will give `level` a "Medium" value, but in our case we are using the struct built-in initiliazer with a specific level attribute set to "Easy".
</details>

---

### 2. What will output when you run it?
```swift
struct Demo {
  let id: Int = -1
}
struct DemoViewModel {
  let demo: Demo
}

let demos = [Demo(), Demo()]
let viewModels = demos.map(DemoViewModel.init)
print(viewModels[0].demo)
```
- [ ] A) Demo(id: -1).
- [ ] B) Demo().
- [ ] C) Demo.self
- [ ] D) Optional(Demo.self).
- [ ] E) Code does not compile.
- [ ] F) Code compiles fine but will crash.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  A) Demo(id: -1). ✅ 

- **Explanation:**  
  `map` requires a closure that takes a type `T` and returns a type `U` (example). `Initializer`s are also a type of `closure`. So we can just say `map(DemoViewModel.init)`.
</details>

---

### 3. What will output when you run it?
```swift
struct Person {
  var height: Double
  lazy var heightMeter: Double = {
    return height / 100
  }()
}
var p = Person(height: 178)
print(p.heightMeter)
p.height = 189
print(p.heightMeter)
```
- [ ] A) 1.78, 1.89.
- [ ] B) 1.78, 1.78.
- [ ] C) Code does not compile.
- [ ] D) Code compiles fine but will crash.
- [ ] E) 1.89, 1.78.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  B) 1.78, 1.78. ✅ 

- **Explanation:**  
  A `lazy stored property` is a property whose initial value is not calculated until the first time it is used. If you wanted to re-calculate its value every time is called, you'd need a `computed` var.
</details>

---

### 4. What will be the value of `c.point` when printed out?
```swift
struct Point {
    var x: Double
    let y: Double
}

struct Coordinates {
    var point: Point {
        didSet {
            point.x = 0
        }
    }
}

var c = Coordinates(point: Point(x: 999, y: 999))
print(c.point)
```
- [ ] A) Point(x: 999.0, y: 999.0).
- [ ] B) Point(x: 0.0, y: 100.0).
- [ ] C) Point(x: 0.0, y: 999.0).
- [ ] D) The code does not compile.
- [ ] E) Code compiles fine but will crash.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  A) Point(x: 999.0, y: 999.0). ✅ 

- **Explanation:**  
  The `didSet` does not get triggered in the initializer, so the c.point will have the original value of `Point(x: 999.0, y: 999.0)`.
</details>

---

### 5. What will output when you run it?
```swift
struct Memory {
    var adventures = [String]()
    func add(__ adventure: String) {
        adventures.append(adventure)
    }
}

var memory = Memory(adventures: ["Climbing 2003"])
memory.add("Climbing 2003")
print(memory.adventures)
```
- [ ] A) Code does not compile.
- [ ] B) Code compiles fine but will crash.
- [ ] C) ["Climbing 2003"].
- [ ] D) ["Climbing 2003", "Climbing 2003"].
- [ ] E) 2.
- [ ] F) "Climbing 2003".

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  A) Code does not compile. ✅ 

- **Explanation:**  
  Structs are value types, by default, props of a value type can't be modified from within its instance methods. You can allow that by declaring the instance methods as mutating: `mutating func add(..)`.
</details>

[🔼 Back to Top](#table-of-contents)

---

## Enumerations

### 6. What will output when you run it?
```swift
enum IceCream {
  case chocolate
  case greenTea
  case double(IceCream, IceCream)
}
print(IceCream.double(.greenTea, .chocolate))
```
- [ ] A) double(IceCream.greenTea, IceCream.chocolate).
- [ ] B) [.greenTea, .chocolate].
- [ ] C) IceCream.double.
- [ ] D) Code does not compile.
- [ ] E) Code compiles fine but will crash.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  D) Code does not compile. ✅ 

- **Explanation:**  
  This is a recursive enumeration, which has another instance of the enumeration as the associated value for one or more of the enumeration cases. To make it work we need to add `indirect` keyword.
</details>

---

### 7. What will output when you run it?
```swift
enum Switch: RawRepresentable {
    case on
    case off
    
    init?(rawValue: Int) {
        self = .on
    }
    
    var rawValue: Int {
        return 1
    }
}

print(Switch.on == Switch.off)
```
- [ ] A) true.
- [ ] B) false.
- [ ] C) Code does not compile.
- [ ] D) Code compiles fine but will crash.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  A) true. ✅ 

- **Explanation:**  
  To compare whether two cases are equal or not the equality operator uses the raw value, which is always `1` for all cases, that means they are recognized as equal.
</details>

---

### 8. What will output when you run it?
```swift
enum Side: RawRepresentable {
    case left
    case right
    
    init?(rawValue: String) {
        self = .left
    }
    
    var rawValue: String {
        return "left"
    }
}

switch Side.right {
case .left: print("left")
case .right: print("right")
}
```
- [ ] A) "left".
- [ ] B) "right".
- [ ] C) Code does not compile.
- [ ] D) Code compiles fine but will crash.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  B) "right". ✅ 

- **Explanation:**  
  Even though all cases have a raw value of "left", switching over an enum doesn't use its raw value for matching. The raw value is used to compare equality, but not switch over an enum.
</details>

[🔼 Back to Top](#table-of-contents)

---

## Control Flow

### 9. What will output when you run it?
```swift
let job = "UI Designer"
switch job {
case "UI Designer":
  fallthrough
case "iOS Dev", "Android Dev":
  print("Mobile Dev")
case "Designer":
  print("Designer")
default:
  print("Free Application")
}
```
- [ ] A) Ul Designer.
- [ ] B) Ul Designer, Mobile Dev.
- [ ] C) Mobile Dev.
- [ ] D) Ul Designer, Free Application.
- [ ] E) Nothing will be printed out.
- [ ] F) Compiles fine but will crash.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  C) Mobile Dev. ✅ 

- **Explanation:**  
  Swift will correctly match the first case "UI Designer", then the fallthrough keyword will cause control to fall into the next case block and print "Mobile Dev".
</details>

---

### 10. What will output when you run it?
```swift
let age = 15
let defaultAge = 18
var knownAge = 0

switch age {
case 1...18:
    knownAge = defaultAge
    fallthrough
case 16:
    knownAge = 16
case 18:
    knownAge = 18
    fallthrough
default:
    knownAge = defaultAge
}
```
- [ ] A) 15.
- [ ] B) 0.
- [ ] C) 18.
- [ ] D) 16.
- [ ] E) Code compiles fine but will crash.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  D) 16. ✅ 

- **Explanation:**  
  The first case that matches is `1...18`, then the `fallthrough` keyword in Swift will make the body of the next case gets executed, so `16` is the right answer.
</details>

---

### 11. What will output when you run it?
```swift
let state: Bool? = false
if !state! {
    defer {
        print("A")
    }
    print("B")
} else {
    print("C")
}
defer {
    print("D")
}

print("E")
```
- [ ] A) ABDE.
- [ ] B) ABED.
- [ ] C) BEAD.
- [ ] D) BAED.
- [ ] E) CDE.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  D) BAED. ✅ 

- **Explanation:**  
  A `defer` block is executed when its surrounding scope ends. Entering the if scope we get "B" then "A" . Successively we get "E" and "D" as the final outer scope has ended.
</details>

[🔼 Back to Top](#table-of-contents)

---

## Closures & Functions

### 12. What will output when you run it?
```swift
var version = 0
var update: (() -> Void)?

func bump(@escaping completion: () -> Void) {
  update = completion
  completion()
  update?()
}

bump { version += 1 }
print(version)
```
- [ ] A) 0.
- [ ] B) 1.
- [ ] C) 2.
- [ ] D) Code does not compile.
- [ ] E) Code compiles fine but will crash.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  D) Code does not compile. ✅ 

- **Explanation:**  
  `@escaping` keyword comes after the colon as it is part of the closure's type.
</details>

---

### 13. What will output when you run it?
```swift
func isAvailable() -> Bool {
  print("Availability check")
  return true
}

func fetchResults(_ result: @autoclosure () -> Bool) {
  print("Fetched results")
}

fetchResults(isAvailable() == true)
```
- [ ] A) "Availability check", "Fetched results".
- [ ] B) "Fetched results", "Availability check".
- [ ] C) "Availability check".
- [ ] D) "Fetched results".
- [ ] E) Code does not compile.
- [ ] F) Code compiles fine but will crash.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  D) "Fetched results". ✅ 

- **Explanation:**  
  `@autoclosure` attribute automatically transform the statement `isAvailable() == true` in a closure that can be called. Since the closure `result` hasn't been called only "Fetched results" is printed.
</details>

---

### 14. What will output after the closure is called?
```swift
struct Processor {
  var a: Int
  var b: Int
  var sum: Int {
    return a + b
  }
}

var processor = Processor(a: 3, b: 5)
let closure = { [processor] in
  print("Sum is \(processor.sum)")
}
processor.b = 20
closure()
```
- [ ] A) Sum is 8.
- [ ] B) Sum is 23.
- [ ] C) Sum is Optional(8).
- [ ] D) Sum is Optional(23).
- [ ] E) Code does not compile.
- [ ] F) Code compiles fine but will crash.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  A) Sum is 8. ✅ 

- **Explanation:**  
  We captured `processor` in a Capture List `[processor]`, this keeps immutable copy of it. Thanks to this copy, any future change to calculator, outside the closure, will not affect the closure.
</details>

---

### 15. What will output when you run it?
```swift
let signs = ["+4", "+8", "+18", ">65"]
let minAges = [4, 8, 18]

let result = zip(signs, minAges).map { $0 }
print(result)
```
- [ ] A) [("+4", 4), ("+8", 8), ("+18", 18)].
- [ ] B) [("+4", 4), ("+8", 8), ("+18", 18), (">65", 0)].
- [ ] C) ["+4", "+8", "+18", nill].
- [ ] D) Code does not compile.
- [ ] E) Code compiles fine but will crash.
- [ ] F) ["+4"，"+8"，"+18"］

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  A) [("+4", 4), ("+8", 8), ("+18", 18)]. ✅ 

- **Explanation:**  
  If the two sequences passed to zip(_:_:) are different lengths, the resulting sequence is the same length as the shorter sequence. We are mapping $0 (the pair) and not $0.0 (signs) here.
</details>

[🔼 Back to Top](#table-of-contents)

---

## Property Wrappers

### 16. What will output when you run it?
```swift
@propertyWrapper
struct HtmlOpenTAG {
  private var tag: String
  init() { self.tag = "" }
  var wrappedValue: String {
    get { return tag }
    set { tag = "<\(tag)>" }
  }
}

struct Tagger {
  @HtmlOpenTAG var openingTag: String
}

var tagger = Tagger()
tagger.openingTag = "html"
print(tagger.openingTag)
```
- [ ] A) "<htm|>".
- [ ] B) "html".
- [ ] C) "<>".
- [ ] D) "".
- [ ] E) Code does not compile.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  C) "<>". ✅ 

- **Explanation:**  
  Although you are giving a value to your property wrapper var, in the set you are setting its initial value which is empty (""). To expect printing "<html>" you'd have `set { tag = "<\(newValue)>" }`.
</details>

---

### 17. What will output when you run it?
```swift
@propertyWrapper
struct Adult {
    private var age: Int
    var projectedValue: Bool
    
    init() {
        self.age = 0
        self.projectedValue = false
    }
    
    var wrappedValue: Int {
        get { return age }
        set {
            age = newValue
            projectedValue = newValue >= 18
        }
    }
}

struct Person {
    @Adult var age: Int
}

var p = Person()
p.age = 20
print(p.$age)
```
- [ ] A) Code does not compile.
- [ ] B) Code compiles fine but will crash.
- [ ] C) 20.
- [ ] D) 20, false.
- [ ] E) true.
- [ ] F) false, 20.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  E) true. ✅ 

- **Explanation:**  
  A property wrapper can  also expose additional functionality through a `projected value`. The name of the projected value is the same as the wrapped value, except it begins with a dollar sign ($).
</details>

[🔼 Back to Top](#table-of-contents)

---

## Type Extensions

### 18. What will output when you run it?
```swift
struct Airline {
  let name: String 
  let priceTags: [String]
  lazy var nameFormatted: String = {
    return "\(name) Company"
  }()
}
extension Airline {
  lazy var isEconomy: Bool = {
    return priceTags.contains("Economy")
  }()
}
let swiftyJet = Airline(
  name: "Swifty", 
  priceTags: ["Economy", "Superior"])
print(swiftyJet.isEconomy)
```
- [ ] A) False.
- [ ] B) True.
- [ ] C) Optional(True).
- [ ] D) Code does not compile.
- [ ] E) Code compiles fine but it will crash during execution.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  D) Code does not compile. ✅ 

- **Explanation:**  
  Swift extensions can't contain stored properties (such as lazy vars ()), to keep it in an extension you'd have to make it a computed property.
</details>

---

### 19. What will output when you run it?
```swift
open class Vehicle: NSObject {
}

class Car: Vehicle {
    let plate: String
    init(_ plate: String) { self.plate = plate }
}

func ==(l: Car, r: Car) -> Bool { return l.plate == r.plate }

let car1: Vehicle = Car("AX2189")
let car2: Vehicle = Car("AX2189")
print(car1 == car2)
```
- [ ] A) true.
- [ ] B) false.
- [ ] C) Code does not compile.
- [ ] D) Code compiles fine but will crash.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  B) false. ✅ 

- **Explanation:**  
  The custom `==` operator is defined for `Car`, but both car1 and car2 are declared to be of type Vehicle which is of type NSObject, therefore this is a pointer comparison.
</details>

---

### 20. What will output when you run it?
```swift
struct Reservation {
    var name: String
}

extension Reservation: ExpressibleByStringLiteral {
    init(_ value: StringLiteralType) {
        self.init(name: value)
    }
}

var reservation: Reservation = "Jeremy"
print(reservation)
```
- [ ] A) Reservation(name: "Jeremy").
- [ ] B) "Jeremy".
- [ ] C) Code does not compile.
- [ ] D) Code compiles fine but will crash.
- [ ] E) Reservation.name("Jeremy").

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  C) Code does not compile. ✅ 

- **Explanation:**  
  To use have our type initialized with a string literal we are required to implement the required initializer which is `init(stringLiteral: StringLiteralType)` and not `init(_:StringLiteralType)`.
</details>

[🔼 Back to Top](#table-of-contents)

---

## Optionals & Collection Types

### 21. What is the value of `numbers`?
```swift
let numbers = Array(1...7)
print(numbers)
```
- [ ] A) Code does not compile.
- [ ] B) Code compiles fine but it will crash.
- [ ] C) 7 different random integers representation.
- [ ] D) [1,2,3,4,5,6,7].
- [ ] E) 1,2,3,4,5,6,7.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  D) [1,2,3,4,5,6,7]. ✅ 

- **Explanation:**  
  `Array` also has an `initializer` whose parameter is a `sequence` and that will be split into the elements of an array of Int in this case producing `[1,2,3,4,5,6,7]`.
</details>

---

### 22. How many items will `trials` array contain after code is executed?
```swift
var trials = [Int]()
trials.reserveCapacity(2)
trials.append(1)
trials.append(2)
trials.append(3)
print(trials.count)
```
- [ ] A) 0.
- [ ] B) 2.
- [ ] C) 3.
- [ ] D) 5.
- [ ] E) Code compiles fine but will crash.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  C) 3. ✅ 

- **Explanation:**  
  `reserveCapacity()` method just gives an indication of how many elements are intended to be stored in an array, but it does not place any  limit on it.
</details>

---

### 23. What will output when you run it?
```swift
let nr: Int?? = .some(nil)
print((nr ?? "-1") ?? "1")
```
- [ ] A) "-1".
- [ ] B) "1".
- [ ] C) nil.
- [ ] D) Optional(nil).
- [ ] E) Optional("-1").
- [ ] F) Code does not compile.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  B) "1". ✅ 

- **Explanation:**  
  This is a nested-optional. .some(nil) gives an object with the value nil. First evaluation passes with nr being Optional(nil). Nex one (vs "1") we have the value unwrapped (nil), so wins "1".
</details>

---

### 24. What will output when you run it?
```swift
var users: [Int: String?] = [
    1: "Marisa",
    2: "Aldo",
    0: nil
]

users[0] = nil
users[1] = nil
let result = users.count
print(result)
```
- [ ] A) Code does not compile.
- [ ] B) Code compiles fine but will crash.
- [ ] C) 1.
- [ ] D) 2.
- [ ] E) 3.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  C) 1. ✅ 

- **Explanation:**  
  Dictionaries have a subscript through which setting their values to `nil` it removes the value from the dictionary. To set nil values we should use `.some(nil)` instead of `nil` for the value.
</details>

---

### 25. What will output when you run it?
```swift
struct Node {
}

func showNode(node: Node?) {
    guard let node = node else {
        print("There is no node")
        return
    }
    print(node)
}

let node: Node?? = .some(nil)
showNode(node: node!)
```
- [ ] A) "There is no node".
- [ ] B) Optional(nil).
- [ ] C) .some(Node?).
- [ ] D) Code does not compile.
- [ ] E) Code compiles fine but will crash.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  D) Code does not compile. ✅ 

- **Explanation:**  
  The else block of a `guard` statement requires an exit path. You can exit with return, `throwing` an exception or calling a `@noreturn`.
</details>

[🔼 Back to Top](#table-of-contents)

---

## Static & Lazy Properties

### 26. What will output when you run it?
```swift
let limit = 0x100
print(limit)
```
- [ ] A) 100.
- [ ] B) 0.
- [ ] C) 4.
- [ ] D) 256.
- [ ] E) Code compiles fine but will crash.
- [ ] F) Code does not compile without specifying the type.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  D) 256. ✅ 

- **Explanation:**  
  When you declare number with `0x` Swift uses it as a `hexadecimal` prefix. And 0x100 is 256 in hexadecimal. 1x(16^2) = 256.
</details>

---

### 27. What will output when you run it?
```swift
class LocationAdapter: NSObject {
    static var lat: Int = {
        // some calculations
        print("lat")
        return 1
    }()
}

print(LocationAdapter.lat)
print(LocationAdapter.lat)
```
- [ ] A) "lat", 1, 1.
- [ ] B) "lat", 1, "lat", 1.
- [ ] C) "lat", "lat", 1, 1.
- [ ] D) "lat", 1.
- [ ] E) The code does not compile.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  A) "lat", 1, 1. ✅ 

- **Explanation:**  
  `lat` property is static but is also enforced to be lazy, which means it is initialized once (hence it prints one time "lat") and its value is returned twice the same but twice, hence prints twice "1".
</details>

---

### 28. What will output when you run it?
```swift
class CellAdapter: NSObject {
    static var width: Int {
        // some calculations
        print("width")
        return 1
    }
}

print(CellAdapter.width)
print(CellAdapter.width)
```
- [ ] A) "width", 1, "width", 1.
- [ ] B) "width", 1.
- [ ] C) "width", 1, 1.
- [ ] D) "width", "width", 1, 1.
- [ ] E) Code does not compile.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  A) "width", 1, "width", 1. ✅ 

- **Explanation:**  
  Static properties can also be computed properties and this is an example of it. The value is re-calculated and hence it prints "width" and returns "1" everytime is called.
</details>

---

### 29. What will output when you run it?
```swift
struct Tech {
    var name: String
}

var techs = [
    Tech(name: "Swift"),
    Tech(name: "iOS")
]

techs = techs.map {
    $0.name += " Test"
    return $0
}

print(techs)
```
- [ ] A) [Tech(name: "Swift Test"), Tech(name: "iOS Test")].
- [ ] B) [Tech(name: "Swift"), Tech(name: "iOS")].
- [ ] C) Code does not compile.
- [ ] D) Code compiles fine but will crash.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  C) Code does not compile. ✅ 

- **Explanation:**  
  Code doesn't compile because left side of mutating operator isn't mutable: '$0' is immutable, is a let. Work in our map, we would need an extra var inside the closure which can be mutated and returned.
</details>

---

### 30. What will output when you run it?
```swift
struct Device {
  static var type = "device"
  var name: String
}

let device = Device(name: "TV")
print(device.type)
```
- [ ] A) "TV".
- [ ] B) "device.
- [ ] C) String.
- [ ] D) Code does not compile.
- [ ] E) Code compiles fine but will crash.

<details>
<summary>Click to reveal the correct answer</summary>

- **Correct Answer:**  
  D) Code does not compile. ✅ 

- **Explanation:**  
  The `type` property has been declared `static`, which means it must be accessed using `Device.type`.
</details>

---

[🔼 Back to Top](#table-of-contents)