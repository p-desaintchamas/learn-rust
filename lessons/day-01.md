# Day 1 — Your toolchain & first program

**Concept:** How Rust code goes from text to a running program, and what a
Cargo project is made of.

Total: ~30 min. Aim for understanding the *shape* of things today, not mastery.

---

### ▶ Watch (~5 min)
"Rust in 100 seconds" (Fireship) for the 10,000-ft view, then skim the intro of
any "Rust tutorial for beginners" clip.
🔎 https://www.youtube.com/results?search_query=rust+in+100+seconds

### 📖 Read (~8 min)
The Rust Book, **Chapter 1** — "Getting Started":
https://doc.rust-lang.org/book/ch01-00-getting-started.html

Focus on: `cargo new`, `cargo run`, `cargo build`, and the difference between the
compiler (`rustc`) and the build tool (`cargo`).

### ⌨️ Practice (~10 min)
Rust and Cargo are already installed in this repo. In a terminal here:

```bash
cargo run          # builds + runs; you should see the banner
cargo build        # just compiles → target/debug/streak
cargo check        # type-checks WITHOUT producing a binary (fast!)
```

Now **break it on purpose** to meet the compiler — your most helpful teacher in
Rust. In `src/main.rs`, delete a semicolon or misspell `println`. Run `cargo run`
and *read the error*. Rust's errors point at the exact spot and usually suggest a
fix. Then put it back.

### 🔨 Build — `streak`, day 1
The project is already seeded (`src/main.rs`). Make it yours: add a second line
so it prints today's intent.

```rust
fn main() {
    println!("streak — day 1. Let's learn some Rust. 🦀");
    println!("Goal: build a focus-tracker while learning the language.");
}
```

Run `cargo run` and confirm both lines print.

### ✅ Checkpoint
- [ ] I can create, build, and run a Cargo project.
- [ ] I know what `cargo check` does and why it's faster than `build`.
- [ ] I read a compiler error and fixed it.

*Tomorrow: variables, mutability, and Rust's scalar types.*
