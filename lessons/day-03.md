# Day 3 — Functions & control flow

**Concept:** Defining functions, the crucial *expression vs statement*
distinction, and `if`/`loop`/`while`/`for`.

---

### ▶ Watch (~5 min)
"Rust functions and control flow" short.
🔎 https://www.youtube.com/results?search_query=rust+functions+control+flow+tutorial

### 📖 Read (~8 min)
Rust Book **3.3**, **3.5** (and skim **3.4**):
- https://doc.rust-lang.org/book/ch03-03-how-functions-work.html
- https://doc.rust-lang.org/book/ch03-05-control-flow.html

The big idea: **a block `{ ... }` is an expression** — its last line *without a
semicolon* is its value. That's why functions return a value by ending with an
expression (no `return` needed), and why `let n = if cond { 1 } else { 2 };` works.

### ⌨️ Practice (~10 min)
A FizzBuzz with a twist — return a `String` from a function:

```rust
fn fizzbuzz(n: u32) -> String {
    if n % 15 == 0 {
        String::from("FizzBuzz")
    } else if n % 3 == 0 {
        String::from("Fizz")
    } else if n % 5 == 0 {
        String::from("Buzz")
    } else {
        n.to_string()
    }
}

fn main() {
    for n in 1..=20 {          // inclusive range
        println!("{}", fizzbuzz(n));
    }
}
```

Note the last line of `fizzbuzz` has **no semicolon** — it's the return value.
Add one and read the error to feel the rule.

### 🔨 Build — `streak`, day 3
Write the function that formats minutes as a human string. You'll reuse this all
month.

```rust
/// Formats a minute count like "30m" or "1h05m".
fn format_minutes(total: u32) -> String {
    let hours = total / 60;
    let mins = total % 60;
    if hours == 0 {
        format!("{mins}m")
    } else {
        format!("{hours}h{mins:02}m")   // :02 → zero-pad to 2 digits
    }
}

fn main() {
    for m in [25, 30, 60, 95, 125] {
        println!("{m:>3} min -> {}", format_minutes(m));
    }
}
```

### ✅ Checkpoint
- [ ] I can write a function with typed parameters and a return type.
- [ ] I can explain why a trailing semicolon changes the meaning of a block.
- [ ] I used a `for` loop over a range and over an array.

*Tomorrow: tuples, arrays, slices, and the String vs &str distinction.*
