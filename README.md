## 型について
### Compound型
プリミティブなCompound型はTupleとArraysの２つ。
Tupleはいろいろな型の値をグループ化するためのもの。
```rust
let tup: (u32, f64, u8) = (400, 6.4, 1);
```

Arraysは同じ型の値のコレクションになる。
```rust
let arr1 = [1,2,3,4,5];

let arr2 = [3; 5]; // same as writing let arr2 = [3,3,3,3,3];

let first = arr1[0]
let second = arr2[1]
```
