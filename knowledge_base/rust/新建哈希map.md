---
tags:
  - rust
---

## 创建一个空的 `HashMap`
```rust
pub fn new() -> HashMap<K, V, RandomState>
```

```rust
use std::collections::HashMap;
let mut map: HashMap<&str, i32> = HashMap::new();
```

## 将键值对插入哈希map
```rust
pub fn insert(&mut self, k: K, v: V) -> Option<V>
```

todo_list













```rust
use std::collections::HashMap;

let mut map = HashMap::new();
assert_eq!(map.insert(37, "a"), None);
assert_eq!(map.is_empty(), false);

map.insert(37, "b");
assert_eq!(map.insert(37, "c"), Some("b"));
assert_eq!(map[&37], "c");
```
