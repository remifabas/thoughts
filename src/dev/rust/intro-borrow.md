# Intro to ownership - borrow-checker

## Ownership

It's really simple to try and create compiler error because of the ownership system in rust !

Let's says we have a simple hello world program:

```rust
fn print_string(s: String) {
    println!("{}", s);
}

fn main() {
    let s = String::from("hello");
    print_string(s);
}
```

The code declare a string, a transmit this string to the function `print_string`

Now let's says we want to call two times the  `print_string` function

~~~admonish bug
```rust
fn print_string(s: String) {
    println!("{}", s);
}

fn main() {
    let s = String::from("hello");
    print_string(s);
    print_string(s);
}
```
This code does not compile. The compiler says two things:
- move occurs because `s` has type `String`, which does not implement the `Copy` trait
- note: consider changing this parameter type in function `print_string` to borrow instead if owning the value isn't necessary
~~~

Copy trait ? borrow instead if owning ? Ok let's take a step back.

In Rust, every value has a variable that's called its owner. There can only be one owner at a time, and when the owner goes out of scope, the value is dropped.

~~~admonish info collapsible=true title="the value is dropped ?"
When a value is "dropped", it means that the memory allocated for that value is freed. Each value has a unique owner, and when the owner goes out of scope, the value is dropped and its memory is freed.

Dropping a value means that the destructor of that value is called. The destructor is responsible for cleaning up any resources that the value might be holding, such as closing file handles or freeing memory.
~~~

```rust
fn main() {
    let s = String::from("hello");
    println!("{}", s);
}
```

In this code, s is the owner of the string "hello". When s goes out of scope at the end of the main function, the memory used to store the string is automatically returned to the system.

When you pass a value to a function, ownership of the value is transferred to the function. For example:
```rust
fn print_string(s: String) {
    println!("{}", s);
}

fn main() {
    let s = String::from("hello");
    print_string(s);
}
```
In this code, ownership of the string "hello" is transferred to the print_string function when it's called. The function takes ownership of the string and then returns ownership to the system when it goes out of scope. So the memory of s is dropped at the end of `print_string` function.

~~~admonish info title="Better vision to this drop thing"
In Rust, we can implement the Drop trait to execute some code when a value is dropped. Here's an example:

```rust
struct MyStruct {
    name: String,
}

impl MyStruct {
    fn new(name: &str) -> Self {
        MyStruct {
            name: String::from(name),
        }
    }
}


impl Drop for MyStruct {
    fn drop(&mut self) {
        println!("MyStruct instance with name '{}' dropped", self.name);
    }
}

fn main() {
    let _s = MyStruct::new("example");
    // `_s` will be dropped at the end of this scope
    println!("End of main function");
}
```
You should see in output 

End of main function  
MyStruct instance with name 'example' dropped  

Now let's tweak the main function and give the ownership of `_s` to a `print_string` function

```rust
struct MyStruct {
    name: String,
}

impl MyStruct {
    fn new(name: &str) -> Self {
        MyStruct {
            name: String::from(name),
        }
    }
}

fn print_string(s: MyStruct) {
    println!("{}", s.name);
}

impl Drop for MyStruct {
    fn drop(&mut self) {
        println!("MyStruct instance with name '{}' dropped", self.name);
    }
}

fn main() {
    let _s = MyStruct::new("example");
    // `s` will be dropped at the end of this scope
    print_string(_s);
    println!("End of main function");
}
```

You should see:

example  
MyStruct instance with name 'example' dropped  
End of main function  

So you can clearly see when the MyStruct _s is dropped and why we can't call two times
`print_string` function
~~~

## Clone

Remember when the compiler says this:

- move occurs because `s` has type `String`, which does not implement the `Copy` trait

If you look at what the compiler says it also tell us that:
help: consider cloning the value if the performance cost is acceptable
  |
7 |     print_string(s.clone());


```rust
fn print_string(s: String) {
    println!("{}", s);
}

fn main() {
    let s = String::from("hello");
    print_string(s.clone());
    print_string(s);
}
```

Here the first `print_string` take the ownership of a deep copy of the string `s` let's says `s'`, and the second `print_string` take the ownership of `s`

## Borrow

Compiler friend also tell us:

- note: consider changing this parameter type in function `print_string` to borrow instead if owning the value isn't necessary

You can also pass ownership of a value to a function temporarily using references. For example:

```rust
fn print_string(s: &String) {
    println!("{}", s);
}

fn main() {
    let s = String::from("hello");
    print_string(&s);
}
```

In this code, a reference to the string is passed to the print_string function instead of the value itself. The function can use the value of the string, but ownership remains with the caller.

If i go back to my code with Drop trait and change the `print_function` to borrow the ownership:

```rust
struct MyStruct {
    name: String,
}

impl MyStruct {
    fn new(name: &str) -> Self {
        MyStruct {
            name: String::from(name),
        }
    }
}

fn print_string(s: &MyStruct) {
    println!("{}", s.name);
}

impl Drop for MyStruct {
    fn drop(&mut self) {
        println!("MyStruct instance with name '{}' dropped", self.name);
    }
}

fn main() {
    let _s = MyStruct::new("example");
    // `s` will be dropped at the end of this scope
    print_string(&_s);
    println!("End of main function");
}
```

output:
example  
End of main function  
MyStruct instance with name 'example' dropped  

`_s` var keep the ownership, `print_function` only borrow the memory and this memory will be drop at the end of the scope of the main function.
