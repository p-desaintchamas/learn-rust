# Day 5 — Ownership I: the heart of Rust

**Concept:** Every value has a single **owner**; when the owner goes out of
scope, the value is dropped. Assigning or passing a heap value **moves** it.
This is how Rust guarantees memory safety with no garbage collector.

Take it slow today — this is *the* idea that makes everything else click.

---

### ▶ Watch (~6 min)
"Rust ownership explained" — watch one carefully.
🔎 https://www.youtube.com/results?search_query=rust+ownership+explained

### 📖 Read (~10 min)
Rust Book **4.1 What Is Ownership?**:
https://doc.rust-lang.org/book/ch04-01-what-is-ownership.html

The three rules:
1. Each value has one owner.
2. There can be only one owner at a time.
3. When the owner goes out of scope, the value is dropped.

**Move vs Copy:** simple stack types (`i32`, `bool`, `char`, tuples of them)
implement `Copy` — assigning duplicates them. Heap types like `String` and `Vec`
**move** — the old binding becomes invalid. Use `.clone()` to deep-copy on purpose.

### ⌨️ Practice (~10 min)
Predict which lines fail, then check in the Playground:

```rust
fn main() {
    let s1 = String::from("focus");
    let s2 = s1;               // MOVE: s1 is now invalid
    // println!("{s1}");       // ❌ uncomment → "value borrowed after move"
    println!("{s2}");          // ✅

    let s3 = s2.clone();       // explicit deep copy
    println!("{s2} and {s3}"); // ✅ both valid

    let n = 5;
    let m = n;                 // COPY (i32 is Copy)
    println!("{n} {m}");       // ✅ both valid — no move
}
```

Then: write `fn consume(s: String)` that prints `s`. Call it with a `String`,
then try to use that string afterward. Read the error. Now change the parameter
to `&str` and pass `&the_string` — notice you can still use it after. That's the
bridge to Day 6 (borrowing).

Optional drill: Rustlings `move_semantics` — https://github.com/rust-lang/rustlings

### 🔨 Build — `streak`, day 5
Make a helper that labels a session by tag, being deliberate about ownership.
Taking `&str` means callers keep their strings.

```rust
fn label(tag: &str, minutes: u32) -> String {
    // We borrow `tag`, and return a newly-owned String.
    format!("[{tag}] {minutes}m")
}

fn main() {
    let tag = String::from("rust");
    let line = label(&tag, 30);   // borrow, don't move
    println!("{line}");
    println!("still own: {tag}"); // ✅ tag wasn't moved
}
```

### ✅ Checkpoint
- [ ] I can state the three ownership rules from memory.
- [ ] I can explain why `let s2 = s1;` invalidates `s1` for `String` but not `i32`.
- [ ] I know that taking `&str`/`&T` borrows instead of moving.

*Next week: borrowing & references, then we start modeling real data with structs.*
