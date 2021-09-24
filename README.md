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

### 式
スコープを作成する{}は式となる。
```rust
let y = {
  let x = 3;
  x + 1;
} //4と評価されるブロック
```

### 関数
```rust
fn test1(x: i32) {
  // something
}

fn test2(x: i32) -> i32 {
  x + 1
  // return x + 1; //return ももちろんOK
  // x + 1; //;をつけると文になるのでコンパイルエラー
}
```

### 制御構文
```rust
if number < 5 {
  println!("condition was true.");
} else {
  println!("condition was false.");
}

// ifは式なので右辺に書ける
let number = if condition {
    5
} else {
    6
};

loop {
  // something
}

while number != 0 {
  // something
}

// コレクションの操作
let a = [10, 20, 30];
for element in a.iter() {
  println!("the value is {}", element);
}
```
