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

---

# Tedium

???

Not difficult, but tedious

---

# Custom Derive
