# Converting strings

Often when writing a function that takes a piece of text you’ll want to support both `String` and `&str` to be more convenient to the caller. This is best achieved by using `&str` or `Into<String>`. 

`String` can be converted to `&str` like this:
```rust,ignore,does_not_compile
let text = String::new();
print(&text);
``` 
(Actually it's converted to `&String` as adding a `&` just makes it a reference but rust treats `&String` as `&str` when passed a parameter)

The Into trait tells the compiler to allow any parameter that be coerced as that type to be passed in. `&str` already has the `Into<String>` trait but it can also be implemented for any struct. `Into<X>` for Y is automatically implemented for any type that implements `From<Y>` for X which is actually how it’s implemented for Strings and is the recommended approach. 

```rust,ignore,does_not_compile
fn print(value: &str) { 
	println!("{}", value;
}

fn print<S: Into<String>>(value: S) { 
	println!("{}", value.into());
}
```
