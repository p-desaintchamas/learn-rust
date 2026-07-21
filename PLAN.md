# Learn Rust in 30 Days — by building `streak`

A weekday-paced plan. **One 30-minute lesson per weekday**, Monday–Friday.
Slow is better than not at all: each lesson is deliberately small so you keep
coming back.

- **Start:** Tue 21 Jul 2026 · **Finish:** Mon 31 Aug 2026 (30 lessons, weekdays only)
- **Daily shape (30 min):** ~5 min video · ~8–10 min reading · **≥10 min hands-on**
- **The project:** `streak` — a focus-session & learning-streak tracker CLI.
  It's *meta*: by the end it tracks the very habit you built learning Rust.

Each morning you get a Focus Time slot on your calendar and that day's lesson.

---

## What you'll be able to do by Day 30

By the end you will have written, tested, documented, and **installed** a real
command-line tool, and you'll be able to:

- Read and write idiomatic Rust, and explain **ownership, borrowing & lifetimes** —
  the thing that makes Rust *Rust*.
- Model data with **structs, enums, and pattern matching**; handle absence and
  failure with **`Option` and `Result`** (no `null`, no exceptions).
- Use **generics, traits, iterators, and closures** to write compact, reusable code.
- Pull in the crate ecosystem: **clap** (CLI), **serde** (JSON), **chrono** (time),
  **anyhow/thiserror** (errors), **toml** (config).
- Read/write files, persist state, and parse command-line arguments.
- Write **unit & integration tests**, generate docs, and pass **clippy** + **fmt**.
- Do basic **concurrency** with threads and channels.
- `cargo install` your own tool and use it for real.

**Your finished `streak` will do:**

```
streak start                 # begin a focus session (optional background timer)
streak log 30 rust           # record a 30-minute session tagged "rust"
streak stats                 # totals, per-tag breakdown, this-week summary
streak status                # current streak & longest streak 🔥
streak heat                  # a GitHub-style focus heatmap in your terminal
```

Where to go next is covered on Day 30 (async/`tokio`, web with `axum`, TUIs, …).

---

## The resources (all free, all canonical)

- **The Rust Book** — https://doc.rust-lang.org/book/ (our spine)
- **Rust by Example** — https://doc.rust-lang.org/rust-by-example/ (runnable snippets)
- **Rustlings** — https://github.com/rust-lang/rustlings (tiny fix-the-code drills)
- **`std` docs** — https://doc.rust-lang.org/std/
- **Videos** — short ones from *Let's Get Rusty*, *Jon Gjengset (Crust of Rust)*,
  and the official Rust channel. The morning message picks and verifies a fresh
  link so you never hit a dead video.

> Tip: keep the [Rust Playground](https://play.rust-lang.org/) open in a tab for
> quick experiments without touching the project.

---

## The 30 lessons

Legend: **Concept** → what you learn · **Read** → Rust Book chapter ·
**Practice** → ≥10 min hands-on · **Project** → what you add to `streak` that day.

### Week 1 — Foundations & tooling

| # | Date | Concept | Read | Practice | Project increment |
|---|------|---------|------|----------|-------------------|
| 1 | Tue 21 Jul | Toolchain: `cargo`, `rustc`, build/run; anatomy of a crate | Ch. 1 | `cargo new`, run, break & fix a compile error | Seed the `streak` crate; print a banner |
| 2 | Wed 22 Jul | Variables, mutability, shadowing, constants; scalar types | Ch. 3.1–3.2 | Experiment with `let`/`mut`/shadowing in the Playground | Add `const SESSION_MINUTES: u32 = 30;` and use it |
| 3 | Thu 23 Jul | Functions, expressions vs statements, control flow | Ch. 3.3–3.5 | A FizzBuzz variant with `for`/`if` | `fn format_minutes(m: u32) -> String` → `"30m"` / `"1h05m"` |
| 4 | Fri 24 Jul | Compound types: tuples, arrays, slices; `String` vs `&str` | Ch. 4.3 | Slice & index arrays; convert `String`↔`&str` | Hold a day's sessions in an array; sum the minutes |
| 5 | Mon 27 Jul | **Ownership I**: move, copy, clone, scope | Ch. 4.1 | Ownership puzzles (Rustlings `move_semantics`) | Pass session tags around without fighting the compiler |

### Week 2 — Ownership, data modeling, errors

| # | Date | Concept | Read | Practice | Project increment |
|---|------|---------|------|----------|-------------------|
| 6 | Tue 28 Jul | **Ownership II**: references & borrowing, `&`/`&mut` | Ch. 4.2 | Rustlings `borrowing`; fix borrow-checker errors | Functions borrow the session list instead of taking it |
| 7 | Wed 29 Jul | Structs, methods, associated fns, `#[derive(Debug)]` | Ch. 5 | Model a `Rectangle`, add methods | Define `struct Session { minutes, tag }` + `impl` |
| 8 | Thu 30 Jul | Enums, `match`, `Option<T>` | Ch. 6 | Rustlings `enums`, `options` | `enum Activity { Reading, Coding, Video }`; label via `match` |
| 9 | Fri 31 Jul | Error handling: `Result`, `?`, `panic!`, `unwrap`/`expect` | Ch. 9 | Parse ints safely; propagate errors with `?` | Parse the "minutes" argument returning `Result` |
| 10 | Mon 3 Aug | Collections I: `Vec<T>` in depth | Ch. 8.1 | Push/iterate/index vectors; handle empties | Store sessions in a `Vec<Session>` |
| 11 | Tue 4 Aug | Collections II: `HashMap`, `String` methods | Ch. 8.2–8.3 | Word-count kata with a `HashMap` | Aggregate minutes **per tag** into a `HashMap` |
| 12 | Wed 5 Aug | Modules & crate layout: `mod`, `pub`, `lib.rs` + `main.rs` | Ch. 7 | Split a toy program into modules | Refactor `streak` into `session` + `stats` modules |

### Week 3 — Traits, iterators, real CLI, tests

| # | Date | Concept | Read | Practice | Project increment |
|---|------|---------|------|----------|-------------------|
| 13 | Thu 6 Aug | Generics & traits (intro) | Ch. 10.1–10.2 | Write a generic `largest`; implement a trait | `trait Report` for anything summarizable |
| 14 | Fri 7 Aug | `Display`/`Debug`, trait bounds, `impl Trait` | Ch. 10.2 | Implement `Display` for a type | `impl Display for Session` → pretty one-liner |
| 15 | Mon 10 Aug | **Iterators & closures**: `map`/`filter`/`fold`/`collect` | Ch. 13 | Rewrite loops as iterator chains | Compute totals & per-tag with iterator chains |
| 16 | Tue 11 Aug | Files & paths: `std::fs`, `std::path` | Ch. 12.1–12.3 | Read a file into lines; write one out | Persist sessions to `~/.streak/log` (one line each) |
| 17 | Wed 12 Aug | **First crate**: `serde` + JSON | Book "Using crates" + serde.rs | Add a dep; derive `Serialize`/`Deserialize` | Store the log as JSON (`~/.streak/log.json`) |
| 18 | Thu 13 Aug | CLI args: `std::env::args`, then **`clap`** | clap docs (derive) | Parse flags/subcommands | `streak start` / `log <min> <tag>` / `stats` subcommands |
| 19 | Fri 14 Aug | Dates & time: **`chrono`** | chrono docs | Format "now"; compute "this week" | Timestamp sessions; filter to today / this week |
| 20 | Mon 17 Aug | **Testing**: unit + integration, `cargo test` | Ch. 11 | Write tests for a pure function | Test the aggregation logic thoroughly |

### Week 4 — Streaks, heatmap, concurrency, ship it

| # | Date | Concept | Read | Practice | Project increment |
|---|------|---------|------|----------|-------------------|
| 21 | Tue 18 Aug | Algorithm day: computing streaks from dates | (recap Ch. 8, 13) | Design current/longest streak on paper then code | `streak status` → current & longest streak 🔥 |
| 22 | Wed 19 Aug | Terminal formatting & ANSI color | Rust by Example: formatting | Print colored blocks | `streak heat` → GitHub-style focus heatmap |
| 23 | Thu 20 Aug | Error handling, matured: `anyhow` + `thiserror` | anyhow/thiserror docs | Replace `unwrap`s with `?` + context | One clean error type across the app |
| 24 | Fri 21 Aug | **Lifetimes** (gentle, applied) | Ch. 10.3 | Rustlings `lifetimes` | A fn returning a borrowed "busiest tag" |
| 25 | Mon 24 Aug | Closures deeper; sorting with comparators | Ch. 13.1 | Sort by multiple keys | Sort tags & sessions by minutes |
| 26 | Tue 25 Aug | Smart pointers (light touch): `Box`, `Rc` | Ch. 15.1, 15.4 | Build a tiny recursive type | Optional: group sessions into a small tree |
| 27 | Wed 26 Aug | **Concurrency**: threads & channels | Ch. 16.1–16.2 | Spawn threads; send over a channel | Background 30-min timer for `streak start` + stop channel |
| 28 | Thu 27 Aug | Config files: **`toml`** + serde | toml docs | Parse a TOML file | `~/.streak/config.toml` (default length, colors) |
| 29 | Fri 28 Aug | Docs & quality: `///`, `cargo doc`, `clippy`, `fmt` | Ch. 14.2 | Document a module; fix all clippy lints | Doc-comment the crate; README; green clippy + fmt |
| 30 | Mon 31 Aug | **Capstone**: integrate, `cargo install`, retrospective | Ch. 20 intro (what's next) | `cargo install --path .`; log this session with your own tool | Ship it; note next steps (async, web, TUI) |

---

## How the daily automation works (so you can tweak it)

- A **Routine** fires each weekday morning (08:00 Europe/Paris) in a fresh session.
- It reads this file + `progress.json`, figures out the next undelivered lesson,
  **books a 30-min Focus Time** on your calendar (a free morning slot, else the
  1:30–2:00 PM lunch window), writes/opens `lessons/day-NN.md`, verifies a video
  link, and sends you the lesson.
- Miss a day? Nothing breaks — the next morning simply serves the next lesson.
  Go faster if you want by opening the next `lessons/day-NN.md` yourself.
- Everything lives in this repo, so the plan is yours to edit.

Progress is tracked in [`progress.json`](./progress.json).
Lessons live in [`lessons/`](./lessons/).
