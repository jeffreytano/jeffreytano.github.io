---
layout: single
title: "Rust Basics"
permalink: /learning/rust/
classes: wide
sidebar:
  nav: Programming
---
## Variables
**Let variable**
```
let variable_name: {type} = "Hello World";
```
 - Data type can be auto detected
 - `let` variable are immutable in default
    - To set mutable ⇒ `let mut variable_name ...`

**Const variable**
```
const VARIABLE_NAME: {type} = 10;
```
`const` can only assigned with const value, no variables

**Tuple**
```
let tuple_name: ({type1}, {type2}) = ({data1}, {data2});// define tuple 

let (d1: {type1}, d2: {type2}) = tuple_name; // destruct tuple
let d1: {type1} = tuple_name.0 // get child from tuple 
```

## String operation
```
println!("printing {}", variable_name);
```
```
format!("formating {}", variable_name);
```
```
let s1: String = String::from("John");
let s2: String = s1;
println!(s1);
println!(s2);
```
which will return compile error since rust use move operation when `let s2 = s1` runs and the string "John" is assigned to s2, so no reference is remained in s1 when `println!(s1)` runs

Make use of reference and pointer operation `&` and `*`

```
let s1: String = String::from("John");
let s2: &String = &s1;
println!(&s1);
println!(s2);
```

## Mutable reference
```
let mut name : String = String::from("John");
let name2: &mut String = &mut name;
let name3: &mut String = &mut name; 
anyFunction(&mut name2);
```
should result in compile error since **at most 1 mutable reference at once** (there are `&mut name` and `&mut name2` at the same time)

## Function
```
fn function_name(parameter) -> returnType{
  ...
}
```

Example for no parameter and return
```
fn function_name(){
  ...
}
```

functions don't need a return statement
instead, return the last statement without `;`

## Inline function
\*inline function can be pointed by a pointer (assign to variables)


```
fn main(){
  let say_hello_to: |&str| -> String = |name: &str| format!("Hello, {}!", name); 
  //this is an inline function
  let full_name: |&str, &str| -> String = |first_name: &str, 
  last_name: &str| format!("{} {}",first_name, last_name); //another inline function
}
```

**Multiple statement inline function**

```
fn main(){
  let ask_for_age: || -> () = || {
    //multiple statement
  }
}
```

**Call back functions**
```
fn process_name(name: &str, callback: fn(&str) -> ()) ->() { 
  callback(name);
}
```
remember to specify the return type of the function being parameter

## Structure

**Basic struct define**
```
struct Person {
  name: String,
  age: u8,
}
```

**Access struct child**
```
println!(Person.name);
```

**Struct update** \
Use spread
```
let person1: Person = Person{
  name: "John",
  age: 30
}

let person2: Person = Person{
  name: "Doe",
  ..person1
}
```
only update specified child while other is remain the same 

**Struct implement**

```
struct Point(f64,f64,f64);

impl Point {
  fn describe(&self) {
    println!("Point is at ({}, {}, {})", self.0, self.1, self.2 );
  }
  fn create_twice(&self) -> Point {
    Point(self.0 * 2.0, self.1 * 2.0, self.2 * 2.0)
  }
  fn make_self_twice(&mut self) { //only work if the caller is mutable
    self.0 *= 2.0;
    self.1 *= 2.0;
    self.2 *= 2.0;
  }
  fn zero() -> Point{
    Point(0.0,0.0,0.0)
  }
}

fn main() {
  let point0: Point = Point::zero();
  let mut point1: Point = Point(1.0,2.0,3.0);
  let point2: Point = point1.create_twice();
  point1.make_self_twice;
  point1.describe();
}
```