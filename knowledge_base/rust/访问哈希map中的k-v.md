---
tags:
  - rust
---

## 通过 `get` 方法并提供对应的键来从哈希 map 中获取值
```rust
    use std::collections::HashMap;

    let mut scores = HashMap::new();

    scores.insert(String::from("Blue"), 10);
    scores.insert(String::from("Yellow"), 50);

    let team_name = String::from("Blue");
    let score = scores.get(&team_name).copied().unwrap_or(0);
```
>这里，`score` 是与蓝队分数相关的值，应为 `10`。`get` 方法返回 `Option<&V>`，如果某个键在哈希 map 中没有对应的值，`get` 会返回 `None`。程序中通过调用 `copied` 方法来获取一个 `Option<i32>` 而不是 `Option<&i32>`，接着调用 `unwrap_or` 在 `scores` 中没有该键所对应的项时将其设置为零。

## 可以使用与 vector 类似的方式来遍历哈希 map 中的每一个k-v
```rust
    use std::collections::HashMap;

    let mut scores = HashMap::new();

    scores.insert(String::from("Blue"), 10);
    scores.insert(String::from("Yellow"), 50);

    for (key, value) in &scores {
        println!("{key}: {value}");
    }
```
这会以任意顺序打印出每一个k-v

## iter迭代器访问k-v
一个迭代器，以任意顺序访问所有K-V。 迭代器元素类型为 `(&'a K, &'a V)`
```rust
use std::collections::HashMap;

let map = HashMap::from([
    ("a", 1),
    ("b", 2),
    ("c", 3),
]);

for (key, val) in map.iter() {
    println!("key: {key} val: {val}");
}
```
- performance：
	在当前实现中，迭代 map 需要 O(capacity) 时间而不是 O(len) 时间，因为它在内部也访问了空的 buckets。


---

## `iter_mut`对值进行可变引用
一个迭代器，以任意顺序访问所有k-v，并且对值进行可变引用。 迭代器元素类型为 `(&'a K, &'a mut V)`
```rust
use std::collections::HashMap;

let mut map = HashMap::from([
    ("a", 1),
    ("b", 2),
    ("c", 3),
]);

// 更新所有值
for (_, val) in map.iter_mut() {
    *val *= 2;
}

for (key, val) in &map {
    println!("key: {key} val: {val}");
}
```
----

## `values`以任意顺序访问所有值的迭代器
```rust
use std::collections::HashMap;

let map = HashMap::from([
    ("a", 1),
    ("b", 2),
    ("c", 3),
]);

for val in map.values() {
    println!("{val}");
}
```
同`iter_mut`，也有`values_mut`