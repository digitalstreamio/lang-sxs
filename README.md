# tour-de-lang

## Overview

toure-de-lang is a point-by-point comparision between 5 modern programming languages. It focuses on main language features as well as a number of library aspects.

## TOC

* Language Basics
  - Variables
  - Control Flow
  - Basic Types
  - Functions
  - Classes
  - Modules
* Language Advanced
  - Closures
  - Generics
  - Enums
  - Pattern Matching
  - Traits
* Library
  - Arrays
  - Collections
  - Error Handling?
  - Futures
  - Json
  - Strings
  - Tuples
  - Testing?

## Language Basics

### Variables

* Scala

``` scala
  val x = 5
  val y: Int = 5
  var z = 5
```

* Kotlin

``` kotlin
  val x = 5
  val y: Int = 5
  var z = 5
```

* Rust

``` rust
  let x = 5;
  let y: i32 = 5;
  let mut z = 5;
```

* Dart

``` dart
  final x = 5;
  final int y = 5;
  var z = 5;
```

* TypeScript

``` typescript
  const x = 5;
  const y: number = 5;
  let z = 5;
```

### Control Flow

* Scala

``` scala
  val max = if (a > b) a else b

  for (item <- collection) {
    // ...
  }

  while (!done) {
    // ...
  }
```

* Kotlin

``` kotlin
  val max = if (a > b) a else b

  for (item in collection) {
    // ...
  }

  while (!done) {
    // ...
  }
```

* Rust

``` rust
  let max = if a > b { a } else { b };

  for item in collection {
    // ...
  }

  while !done {
    // ...
  }
```

* Dart

``` dart
  final max = a > b ? a : b;
  
  for (var item in collection) {
    // ...
  }      

  while (!done) {
    // ...
  }
```

* TypeScript

``` typescript
  let max;
  if (a > b) {
    max = a;
  } else {
    max = b;
  }

  for (let item in collection) {
    // ...
  }

  while (!done) {
    // ...
  }
```

### Basic Types

* Scala

    Byte, Short, Int, Long, Float, Double, Boolean, Char, Unit 

* Kotlin

    Byte, Short, Int, Long, Float, Double, Boolean, Char, Unit

* Rust

    i8, i16, i32, i64, u8, u16, u32, u64, isize, usize, f32, f64, bool, char, ()

* Dart

    int, double, bool, String, void

* TypeScript

    number, boolean, string, void

### Functions

* Scala

``` scala
  def sum(a: Int, b: Int): Int = {
    a + b
  }
```

* Kotlin

``` kotlin
  fun sum(a: Int, b: Int): Int {
    return a + b
  }
```

* Rust

``` rust
  fn sum(a: i32, b: i32) -> i32 {
    a + b
  }
```

* Dart

``` dart
  int sum(int a, int b) {
    return a + b;
  }
```

* TypeScript

``` typescript
  function sum(a: number, b: number): number {
    return a + b;
  }
```

### Classes

* Scala

``` scala
  class Circle(val x: Double, val y: Double, val radius: Double) {

    def area(): Double = {
      Math.PI * (radius * radius)
    }
  }

  object Circle {
    def apply(x: Double, y: Double, radius: Double): Circle = {
      new Circle(x, y, radius)
    }
  }
```

* Kotlin

``` kotlin
  class Circle(val x: Double, val y: Double, val radius: Double) {
    fun area(): Double {
      return Math.PI * (radius * radius)
    }

    companion object {
      fun create(): Circle = Circle(0.0, 0.0, 2.0)
    }
  }
```

* Rust

``` rust
  struct Circle {
    x: f64,
    y: f64,
    radius: f64,
  }

  impl Circle {
    fn new(x: f64, y: f64, radius: f64) -> Circle {
      Circle {
        x,
        y,
        radius,
      }
    }

    fn area(&self) -> f64 {
      std::f64::consts::PI * (self.radius * self.radius)
    }
  }
```

* Dart

``` dart
  import 'dart:math' as math;

  class Circle {
    const Circle(this.x, this.y, this.radius);

    final double x;
    final double y;
    final double radius;

    double area() {
      return math.pi * (radius * radius);
    }
  }
```

* TypeScript

``` typescript
  class Circle {
    x: number;
    y: number;
    radius: number;

    constructor(x: number, y: number, radius: number) {
      this.x = x;
      this.y = y;
      this.radius = radius;
    }

    area(): number {
      return Math.PI * (this.radius * this.radius);
    }
  }
```

### Modules

* Scala

``` scala
  package io.digitalstream {

    import self.deeply.nested.Utils.{foo => bar}

    object Modules {
      def run(): Unit = {
        bar()
      }
    }

    package self.deeply.nested {

      object Utils {
        def foo(): Unit = {
          println("called `deeply::nested::foo()`")
        }
      }

    }

  }
```

* Kotlin

``` kotlin
  package io.digitalstream

  import io.digitalstream.Utils.foo as bar

  object Modules {

    fun run() {
      bar()
    }
  }

  object Utils {
    fun foo(): Unit {
      println("called `deeply::nested::foo()`")
    }
  }
```

* Rust

``` rust
  use self::deeply::nested::foo as bar;

  pub fn run() {
    bar();
  }

  mod deeply {
    pub mod nested {
      pub fn foo() {
        println!("called `deeply::nested::foo()`")
      }
    }
  }
```

* TypeScript

``` typescript
  export function run(): void {
    Deeply.Nested.foo();
  }

  namespace Deeply {
    export namespace Nested {
      export function foo() {
        console.log("called `deeply::nested::foo()`");
      }
    }
  }
```

## Language Advanced

### Closures

* Scala

``` scala
  val num = 5
  val plusNum = (x: Int) => x + num
```

* Kotlin

``` kotlin
  val num = 5
  val plusNum = { x: Int -> x + num }
```

* Rust

``` rust
  let num = 5;
  let plus_num = |x: i32| x + num;
```

* Dart

``` dart
  final n = 5;
  final plusNum = (int x) => x + n;
```

* TypeScript

``` typescript
  const num = 5;
  let plus_num = (x: number) => x + num;
```

### Generics

* Scala

``` scala
  class Point[T](val x: T, val y: T) {
    def swap(): Point[T] = {
      new Point(y, x)
    }
  }
```

* Kotlin

``` kotlin
  class Point<T>(val x: T, val y: T) {
    fun swap(): Point<T> {
      return Point(y, x)
    }
  }
```

* Rust

``` rust
  struct Point<T: Clone> {
    x: T,
    y: T,
  }

  impl<T: Clone> Point<T> {
    fn swap(&self) -> Point<T> {
      Point { x: self.y.clone(), y: self.x.clone() }
    }
  }
```

* Dart

``` dart
  class Point<T> {
    const Point(this.x, this.y);

    final T x;
    final T y;

    Point<T> swap() {
      return Point(y, x);
    }
  }
```

* TypeScript

``` typescript
  class Point<T> {
    x: T;
    y: T;

    constructor(x: T, y: T) {
      this.x = x;
      this.y = y;
    }

    swap(): Point<T> {
      return new Point(this.y, this.x);
    }
  }
```

### Enums

* Scala

``` scala
  sealed trait Option[+A]
  case object None extends Option[Nothing]
  case class Some[+A](get: A) extends Option[A]
```

* Kotlin

``` kotlin
  sealed class Option<T> {
    class None<T> : Option<T>()
    class Some<T>(val value: T) : Option<T>()
  }
```

* Rust

``` rust
  enum Option<T> {
    Some(T),
    None,
  }
```

* Dart

``` dart
  abstract class Option<T> {
    T get value;
    bool get has;
  }

  class Some<T> implements Option<T> {
    const Some(this.value);

    @override
    final T value;
    @override
    final bool has = true;
  }

  class None<T> implements Option<T> {
    const None();

    @override
    final T value = null;
    @override
    final bool has = false;
  }
```

* TypeScript

``` typescript
  class Some<T> {
    value: T;
    constructor(value: T) {
      this.value = value;
    }
  }

  class None {}

  type Option<T> = Some<T> | None;
```

### Pattern Matching

* Scala

``` scala
  val option = Option("string")
  option match {
    case Some(value) => println(s"got value: $value")
    case None => println("got none")
  }
```

* Kotlin

``` kotlin
  val option = Option.Some("string")
  when (option) {
    is Option.Some -> println("got value: ${option.value}")
    is Option.None<*> -> println("got none")
  }
```

* Rust

``` rust
  let option = Some("string");
  match option {
    Some(value) => println!("got value: {}", value),
    None => println!("got none"),
  }
```

* Dart

``` dart
  final option = Some("string");
  if (option is Some) {
    print("got value: ${option.value}");
  } else if (option is None) {
    print("got none");
  }
```

* TypeScript

``` typescript
  if (option instanceof Option.Some) {
    console.log(`got value: ${option.value}`);
  } else if (option instanceof Option.None) {
    console.log("got none");
  }
```

### Traits

* Scala

``` scala
  trait Similarity {
    def isSimilar(x: Any): Boolean
    def isNotSimilar(x: Any): Boolean = !isSimilar(x)
  }
```

* Kotlin

``` kotlin
  interface Similarity {
    fun isSimilar(x: Any): Boolean
    fun isNotSimilar(x: Any): Boolean = !isSimilar(x)
  }
```

* Rust

``` rust
  TODO any
  trait Similarity {
    fn isSimilar(&self, x: Any) -> bool;
    fn isNotSimilar(&self, x: Any) -> bool { !isSimilar(x) }
  }
```

* Dart

``` dart
  abstract class Similarity {
    bool isSimilar(Object x);
    bool isNotSimilar(Object x) => !isSimilar(x);
  }
```

* TypeScript

``` typescript
  TODO
```

## Library

### Arrays

* Scala

``` scala
  val xs = Array(1, 2, 3)
  val ys = Array.fill(20)(0)
  val x = xs(0)
  val length = xs.length
```

* Kotlin

``` kotlin
  val xs = arrayOf(1, 2, 3)
  val ys = Array(20, { i -> 0 })
  val x = xs[0]
  val length = xs.size
```

* Rust

``` rust
  let xs = [1, 2, 3];
  let ys = [0; 20];
  let x = xs[0];
  let length = xs.len();
```

* Dart

``` dart
  final xs = [1, 2, 3];
  final ys = List<int>.generate(20, (i) => 0);
  final x = xs[0];
  final length = xs.length;
```

* TypeScript

``` typescript
  const xs = [1, 2, 3];
  const x = xs[0];
  const length = xs.length;
```

### Collections

* Scala

``` scala
  names
    .filter(_.startsWith("a"))
    .map(_.toUpperCase())
    .foreach(println)
```

* Kotlin

``` kotlin
  names
    .filter { it.startsWith("a") }
    .map(String::toUpperCase)
    .forEach(::println)
```

* Rust

``` rust
  let result = names.iter()
    .filter(|&it| it.starts_with("a"))
    .map(|&it| it.to_uppercase());
  for item in result {
    println!("{}", item)
  }
```

* Dart

``` dart
  final list = ['apples', 'bananas', 'oranges'];
  list
    .where((it) => it.startsWith("a"))
    .map((it) => it.toUpperCase())
    .forEach((item) => print("$item"));
```

* TypeScript

``` typescript
  names
    .filter(it => it.startsWith("a"))
    .map(it => it.toUpperCase())
    .forEach(it => console.log(it));
```

### Futures

* Scala

``` scala
  Promise.successful("string").future
    .map(_.length)
    .onComplete {
      case Success(res) => println(s"promise succeeded $res")
      case Failure(ex) => println(s"promise failed $ex")
    }
```

* Kotlin

``` kotlin
  CompletableFuture.completedFuture("string")
    .thenApply { res ->
      res.length
    }
    .whenComplete { res, ex ->
      if (ex == null) {
        println("promise succeeded $res")
      } else {
        println("promise failed $ex")
      }
    }
```

* Rust

``` rust
  finished::<String, u32>("string".to_string())
    .map(|res| res.len())
    .then(|res| {
      match res {
        Ok(res) => println!("promise succeeded {}", res),
        Err(ex) => println!("promise failed {}", ex),
      }
      res
    })
    .wait();
```

* Dart

``` dart
  try {
    final res = await Future.value("string");
    print("succeeded $res");
  } catch (ex) {
    print("failed $ex");
  }
```

* TypeScript

``` typescript
  let promise = new Promise<string>((resolve, reject) => {
    resolve('string');
  });
  promise
    .then((res) => {
      return res.length;
    })
    .then((res) => {
        console.log(`promise succeeded ${res}`);
    })
    .catch((reason) => {
        console.log(`promise failed ${reason}`);
    });
```

### Json

* Scala

``` scala
  case class Point(x: Float, y: Float)

  trait PointProtocol extends DefaultJsonProtocol {
    implicit val pointFormat = jsonFormat2(Point)
  }

  val point = Point(1.0f, 2.0f)
  val serialized = pointFormat.write(point);
  println(s"serialized = ${serialized.compactPrint}")
  val deserialized = pointFormat.read(serialized)
  println(s"deserialized = $deserialized")
``` 

* Kotlin

``` kotlin
  data class Point(val x: Float, val y: Float)

  val gson = Gson()
  val point = Point(1.0f, 2.0f)
  val serialized = gson.toJson(point)
  println("serialized = $serialized")
  val deserialized = gson.fromJson<Point>(serialized)
  println("deserialized = $deserialized")
```

* Rust

``` rust
  #[derive(Serialize, Deserialize, Debug)]
  struct Point {
      x: i32,
      y: i32,
  }

  let point = Point { x: 1.0, y: 2.0 };
  let serialized = serde_json::to_string(&point).unwrap();
  println!("serialized = {}", serialized);
  let deserialized: Point = serde_json::from_str(&serialized).unwrap();
  println!("deserialized = {:?}", deserialized);
```

* Dart

``` dart
  import 'dart:convert';

  class Point {
    const Point(this.x, this.y);

    final double x;
    final double y;
    
    factory Point.fromJson(Map<String, dynamic> json) {
      return Point(
        x: json['x'],
        y: json['y'],
      );
    }

    Map<String, dynamic> toJson() => {
        'x': x,
        'y': y,
      };            
  }

  final point = Point(1.0, 2.0);
  final serialized = json.encode(point);
  print("serialized = $serialized");
  final deserialized = Point.fromJson(json.decode(serialized));
  print("deserialized = $deserialized");
``` 

* TypeScript

``` typescript
  interface Point {
    x: number;
    y: number;
  }

  let point: Point = { x: 1.0, y: 2.0};
  let serialized = JSON.stringify(point);
  console.log(`serialized = ${serialized}`);
  let deserialized = JSON.parse(serialized) as Point;
  console.log(`deserialized = Point(${deserialized.x}, ${deserialized.y})`);
```

### Strings

* Scala

``` scala
  val hello = "Hello "
  val world = new String("world!")
  val helloWorld = hello + world
  println(helloWorld)
```

* Kotlin

``` kotlin
  val hello = "Hello "
  val world = "world!".toString()
  val helloWorld = hello + world
  println(helloWorld)
```

* Rust

``` rust
  let hello = "Hello ".to_string();
  let world = "world!".to_string();
  let hello_world = hello + &world;
  println!("{}", hello_world);
```

* Dart

``` dart
  final hello = "Hello ";
  final world = "world!".toString();
  final helloWorld = hello + world;
  print(helloWorld);
```

* TypeScript

``` typescript
  const hello = "Hello ";
  const world = "world!".toString();
  const helloWorld = hello + world;
  console.log(helloWorld);
```

### Tuples

* Scala

``` scala
  val tuple = (1, "hello")
  val tuple2: Tuple2[Int, String] = (1, "hello")
  println(s"tuple ${tuple._1}, ${tuple._2}")
```

* Kotlin

``` kotlin
  val tuple = Pair(1, "hello")
  val tuple2: Pair<Int, String> = Pair(1, "hello")
  println("tuple ${tuple.first}, ${tuple.second}")
```

* Rust

``` rust
  let tuple = (1, "hello");
  let tuple2: (i32, &str) = (1, "hello");
  println!("tuple {}, {}", tuple.0, tuple.1)
```

* Dart

``` dart
  final tuple = [1, "hello"];
  final List<Object> tuple2 = [1, "hello"];
  print("tuple ${tuple[0]}, ${tuple[1]}");
```

* TypeScript

``` typescript
  let tuple = [1, "hello"];
  let tuple2: [number, string] = [1, "hello"];
  console.log(`tuple ${tuple[0]}, ${tuple[1]}`);
```

## Reference

### Dart

- https://dart.dev/guides/language/language-tour

### Kotlin

- https://kotlinlang.org/docs/reference/basic-types.html

### Rust Book

- https://doc.rust-lang.org/book/

### TypeScript

- https://code.visualstudio.com/docs/languages/typescript
