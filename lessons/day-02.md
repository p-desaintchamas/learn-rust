# Day 2 — Variables, mutability & scalar types

**Concept:** Rust variables are immutable by default. You opt into change with
`mut`. Plus the basic number/bool/char types.

---

### ▶ Watch (~5 min)
"Rust variables and mutability" — any short clip (Let's Get Rusty has a good one).
🔎 https://www.youtube.com/results?search_query=rust+variables+mutability+let+mut

### 📖 Read (~8 min)
Rust Book **3.1 Variables and Mutability** and **3.2 Data Types**:
- https://doc.rust-lang.org/book/ch03-01-variables-and-mutability.html
- https://doc.rust-lang.org/book/ch03-02-data-types.html

Key ideas: `let` (immutable), `let mut` (mutable), **shadowing** (re-`let` the
same name, even changing its type), and `const` (compile-time constant, always
typed, SCREAMING_CASE).

### ⌨️ Practice (~10 min)
In the [Playground](https://play.rust-lang.org/), predict then check each result:

```rust
fn main() {
    let x = 5;
    // x = 6;              // ❌ why does this fail? uncomment to see the error
    let mut y = 5;
    y = 6;                 // ✅ ok — y is mut
    let spaces = "   ";
    let spaces = spaces.len(); // ✅ shadowing: &str → usize, same name
    println!("x={x}, y={y}, spaces={spaces}");

    let big: u64 = 1_000_000;   // underscores are just readability
    let ratio = 3.0_f64 / 7.0;  // f64 float
    let yes: bool = big > 10;
    let heart = '❤';            // char is a Unicode scalar, 4 bytes
    println!("{big} {ratio:.3} {yes} {heart}");
}
```

Then: try assigning a `u8` the value `256` and read the compiler's reaction.

### 🔨 Build — `streak`, day 2
Introduce your first constant — the length of a focus session — and use it.

```rust
const SESSION_MINUTES: u32 = 30;

fn main() {
    let sessions_today: u32 = 2;               // immutable for now
    let total = sessions_today * SESSION_MINUTES;
    println!("streak — a {SESSION_MINUTES}-minute focus per session.");
    println!("{sessions_today} sessions today = {total} minutes focused.");
}
```

### ✅ Checkpoint
- [ ] I can explain why `let x = 5; x = 6;` fails but `let mut` fixes it.
- [ ] I know the difference between shadowing and mutation.
- [ ] I've used `const` and a few scalar types (`u32`, `f64`, `bool`, `char`).

*Tomorrow: functions and control flow.*
