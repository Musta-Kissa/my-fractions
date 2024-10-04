### Description
This is an implementation of a Fraction type in Rust

### How to use
#### Cargo.toml
```toml
[dependencies]
my_fractions = { path = "../my_fractions" }
```
##### main/src.rs
```rust
use my_fractions::*;

fn main() {
    println!("{}",fr!(2,3));
}
```
### What it provides
#### Macro
It provides a macro `fr!(2,3)` that is a shorthand for `MyFraction::new(2,3)` 
#### Methods
There are two public methods provided:
- `as_f64()` that returns the approximation of the fraction as a `f64` type
- `as_mixed()` that returns a string of the fraction written in the [mixed numbers](https://en.wikipedia.org/wiki/Fraction#Mixed_numbers) representation 
#### Traits
This type provides implementations for these Traits:
```rust 
impl Sub<MyFraction> for MyFraction {...}
impl Sub<$type> for MyFraction {...}
impl Sub<MyFraction> for $type {...}

impl Add<MyFraction> for MyFraction {...}
impl Add<$type> for MyFraction {...}
impl Add<MyFraction> for $type {...}

impl Mul<MyFraction> for MyFraction {...}
impl Mul<$type> for MyFraction {...}
impl Mul<MyFraction> for $type {...}

impl Div<MyFraction> for MyFraction {...}
impl Div<MyFraction> for $type {...}
impl Div<$type> for MyFraction {...}

impl SubAssign for MyFraction {...}
impl AddAssign for MyFraction {...}
impl SubAssign<$type> for MyFraction {...}
impl AddAssign<$type> for MyFraction {...}

impl PartialEq for MyFraction {...}
impl PartialOrd for MyFraction {...}
impl Ord for MyFraction {...}

impl PartialEq<$type> for MyFraction {...}
impl PartialOrd<$type> for MyFraction {...}
impl PartialEq<MyFraction> for $type {...}
impl PartialOrd<MyFraction> for $type {...}

impl From<$type> for MyFraction {...}

impl Display for MyFraction {...}
```
The `$type` stands for all of `usize, i8, i16, i32, i64, i128, u8, u16, u32, u64, u128` these types

### Examples
```rust
use my_fractions::*;

fn main() {
    let mut fr = MyFraction::new(2, 3);
    println!("{fr}");//(2/3)   
    fr = fr * 5;
    println!("{}",fr);//(10/3)
    println!("{}",fr.as_mixed());//3(1/3)
    fr = fr * 0;
    println!("{}",fr);//0
    fr += 7;
    println!("{}",fr);//7
    fr = fr / 2;
    println!("{}",fr);//(7/2)
    fr -= 2;
    println!("{}",fr);//(3/2)
    println!("{}",fr < 9);//true
    println!("{}",fr < fr!(1,2));//false
    println!("{}",fr == fr!(3,2));//true
 
    println!("{}",fr.as_f64());//1.5
    println!("{}",fr!(3,9).as_f64());//0.3333333333333333
}
```
