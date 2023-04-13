# Example of borrow-checker - ownership case

## Iterate HashMap and update value

Iterate over a HashMap and modify the values, but you need to be careful because Rust's borrow checker will prevent you from doing so in certain situations.

One way to modify values in a HashMap while iterating over it is to use the HashMap::entry method to get a mutable reference to the value, and then modify the value using the mutable reference.

Ok let's say i want to iterate through a map, here is a naive solution:

~~~admonish bug
This will no work in rust, you can launch this code  here in this  browser and see the error:
```rust
use std::collections::HashMap;

fn main() {
    let mut my_map = HashMap::new();

    my_map.insert("foo", 1);
    my_map.insert("bar", 2);

    for (k, v) in my_map {
        my_map[k] = v + 1;
    }

    println!("{:?}", my_map);
}
```
~~~

As you can see with `for (key, value) in my_map`  the ownership of `my_map` is moved due to the implicit call to `.into_iter()` with the `for ... in` statement.
Then

```admonish info
my_map[k] = v + 1;  
^^^^^^ value borrowed here after move
```
when we try to update the map we need to borrow the ownership of the map. But as the ownership to the map gas already been given to`.into_iter()` you're stuck

```admonish 
You can also see that `HashMap<&str, i32>`, which does not implement the `Copy` trait.
Indeed if we could copy the hashmap we could iter throught the first and update the new one.
```


So how can we do our stuff ?

~~~admonish success
use std::collections::HashMap;

```rust
use std::collections::HashMap;

fn main() {
    let mut my_map = HashMap::new();

    my_map.insert("foo", 1);
    my_map.insert("bar", 2);

    for (_k, v) in my_map.iter_mut() {
        *v += 1;
    }

    println!("{:?}", my_map);
}
```

In this example, we first create a HashMap and insert two key-value pairs into it. Then, we use the iter_mut method to iterate over the map's values, getting mutable references to each value. We can then modify each value using the mutable reference.

Note that we use the * operator to dereference the mutable reference and modify the value it points to.

~~~

We can create a new HashMap with the modified key-value pairs and replace the old HashMap with the new one.

Here's an example:

```rust
use std::collections::HashMap;

fn main() {
    let mut my_map = HashMap::new();

    my_map.insert("foo", 1);
    my_map.insert("bar", 2);

    let new_map: HashMap<_, _> = my_map
        .into_iter()
        .map(|(key, mut value)| {
            if key.starts_with("b") {
                value += 1;
            }
            (key, value)
        })
        .collect();

    println!("{:?}", new_map);
}
```

In this example, we use into_iter to consume the original HashMap and create a new one with modified key-value pairs. The closure passed to map takes ownership of each key-value pair, and modifies the value if the key starts with the letter "b". Finally, collect is called to create a new HashMap from the modified key-value pairs.

~~~admonish note collapsible=true title="Booooo ! Way to slow with large Map! 😈😈"
Note that this approach creates a new HashMap, so if the original HashMap is large, it may not be the most efficient solution. If efficiency is a concern, you can use a mutable HashMap and modify the values in place using HashMap::entry.
~~~

You can modify the HashMap in place using the HashMap::retain method. The retain method takes a closure that operates on the key-value pairs of the HashMap and removes any pairs for which the closure returns false.

```rust
use std::collections::HashMap;

fn main() {
    let mut my_map = HashMap::new();

    my_map.insert("foo", 1);
    my_map.insert("bar", 2);

    my_map.retain(|key, value| {
        *value += 1;
        key.starts_with("b")
    });

    println!("{:?}", my_map);
}
```

In this example, we use the retain method to modify the HashMap in place. The closure passed to retain takes mutable references to the key and the value, and we can modify the value using the mutable reference.

The closure also returns a bool indicating whether the key-value pair should be kept or removed. In this example, we only keep the pairs whose keys start with the letter "b". The pairs whose keys start with "f" are removed from the HashMap.

Note that this approach works because we're modifying the HashMap in place, but we're not modifying the keys themselves. If you need to modify the keys as well, you'll need the solution with two loops.
