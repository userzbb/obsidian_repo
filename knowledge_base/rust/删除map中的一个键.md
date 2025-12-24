---
tags:
  - rust
created: Sat, 2025/11/29, 14:07:43
modified: Sat, 2025/11/29, 18:11:18
---

## `remove`
从 map 中删除一个键，如果该键以前在 map 中，则返回该键的值。

键可以是 map 键类型的任何借用形式，但是借用形式上的 [`Hash`](https://rustwiki.org/zh-CN/std/hash/trait.Hash.html "trait std::hash::Hash") 和 [`Eq`](https://rustwiki.org/zh-CN/std/cmp/trait.Eq.html "trait std::cmp::Eq") 必须与键的类型匹配。
```rust
use std::collections::HashMap;

let mut map = HashMap::new();
map.insert(1, "a");
assert_eq!(map.remove(&1), Some("a"));
assert_eq!(map.remove(&1), None);
```

## `remove_entry`
从 map 中删除一个键，如果该键以前在 map 中，则返回存储的K-V。

键可以是 map 键类型的任何借用形式，但是借用形式上的 [`Hash`](https://rustwiki.org/zh-CN/std/hash/trait.Hash.html "trait std::hash::Hash") 和 [`Eq`](https://rustwiki.org/zh-CN/std/cmp/trait.Eq.html "trait std::cmp::Eq") 必须与键的类型匹配。
```rust
use std::collections::HashMap;

let mut map = HashMap::new();
map.insert(1, "a");
assert_eq!(map.remove_entry(&1), Some((1, "a")));
assert_eq!(map.remove(&1), None);
```
