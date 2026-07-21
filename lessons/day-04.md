# Day 4 — Compound types: tuples, arrays, slices, strings

**Concept:** Grouping values (tuples, arrays), borrowing a view into them
(slices), and the two string types everyone trips on: `String` vs `&str`.

---

### ▶ Watch (~5 min)
"Rust String vs &str" — this distinction is worth a dedicated clip.
🔎 https://www.youtube.com/results?search_query=rust+string+vs+str+slice

### 📖 Read (~10 min)
Rust Book **4.3 The Slice Type** (and revisit the "Data Types" compound section):
- https://doc.rust-lang.org/book/ch04-03-slices.html

Mental model:
- **Tuple** `(a, b)` — fixed-size, mixed types, access with `.0`, `.1`.
- **Array** `[T; N]` — fixed-size, same type, lives on the stack.
- **Slice** `&[T]` / `&str` — a *borrowed view* (pointer + length) into an array,
  `Vec`, or `String`. It owns nothing.
- **`String`** — growable, heap-owned text. **`&str`** — a borrowed string slice.
  Prefer taking `&str` in function parameters; return `String` when you own it.

### ⌨️ Practice (~10 min)
```rust
fn main() {
    let point = (3, 4);
    let (x, y) = point;                 // destructuring
    println!("x={x} y={y} first={}", point.0);

    let mins = [25, 30, 45, 60, 20];    // [i32; 5]
    let first_three = &mins[0..3];      // a slice: &[i32]
    println!("slice = {first_three:?}, len = {}", first_three.len());

    let owned: String = String::from("focus");
    let view: &str = &owned;            // borrow a &str from a String
    println!("{} has {} bytes", view, view.len());
}
```

Then write `fn sum(xs: &[u32]) -> u32` that sums a slice, and call it with
`&mins`. Taking `&[u32]` means it works for arrays *and* vectors later.

### 🔨 Build — `streak`, day 4
Represent a day's sessions as an array and total them with a slice function.

```rust
fn total(minutes: &[u32]) -> u32 {
    let mut sum = 0;
    for &m in minutes {          // &m pattern copies each u32 out
        sum += m;
    }
    sum
}

fn main() {
    let today = [30u32, 30, 45];
    println!("{} sessions, {} min total", today.len(), total(&today));
}
```

(You'll replace that manual loop with an iterator on Day 15 — for now, feel the
mechanics.)

### ✅ Checkpoint
- [ ] I can destructure a tuple and index an array.
- [ ] I can explain what a slice is and why `&[T]` is a flexible parameter type.
- [ ] I know when I'd use `String` vs `&str`.

*Monday: the big one — ownership.*
