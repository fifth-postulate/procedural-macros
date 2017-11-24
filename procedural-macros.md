class: center, middle

# Procedural Macros

--

## AKA Custom Derive 

--

At least for now

---

# Disclaimer

.center[![The Rust Logo](image/rust-logo-512x512.png)]

???

* I am not going to teach you Rust
* I am not affiliated with Rust or Mozilla 

---
background-image: url('image/stranger_things.jpg')
background-size: contain

# Story 

???

Role playing is what I regularly do
---

# Code

```rust
fn main() {
    let friends = gurps_friends();

    for friend in friends {
        println!("{}", friend);
    }
}
```

--

```rust
fn gurps_friends() -> Vec<Friend> {
    let mut friends = Vec::new();

    friends.push(marcel());
    friends.push(meron());
    friends.push(mink());
    friends.push(paul());
    friends.push(robin());
    friends.push(sep());

    friends
}
```

???

When `friends` get out of scope, what happens?

---

```rust
pub trait Drop {
    fn drop(&mut self);
}
```

???

Drop is called when a value get's out of scope

--

```rust
impl Drop for Friend {
    fn drop(&mut self) {
        println!("Friend dropped");
    }
}
```

???

An implementation of `Drop` for `Friend`

---

# Tedium

???

Not difficult, but tedious

---

# Custom Derive

???

Custom derive allows you to "derive" an implementation. But how?

---

# Demo

???

The code for this project can be found at [github](https://github.com/fifth-postulate/procedural-macros-code)


---

# Summary

* custom derive for crate `foo` in `foo-derive`
* Must be top-level
* `[lib] proc-macro = true`
* `#[proc_macro_derive(Foo)]`
* `syn` and `quote`

???

* Is a custom
* For now, can change in the future
* It is the law
* Signals custom derive, function is the implementation
* These are your friends

---

# Links

* Presentation: [https://fifth-postulate.github.io/procedural-macros](https://fifth-postulate.github.io/procedural-macros)
* Code: [https://github.com/fifth-postulate/procedural-macros-code](https://github.com/fifth-postulate/procedural-macros-code)
* syn: [https://github.com/dtolnay/syn](https://github.com/dtolnay/syn)
* quote: [https://github.com/dtolnay/quote](https://github.com/dtolnay/quote)
