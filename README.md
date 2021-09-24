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

### 所有権
所有権を有する変数がスコープ外となる際にdropが呼ばれる。
プリミティブ型でない場合、変数へ代入すると代入元から代入先へ所有権が移行する。
以下のコードはs1からs2に所有権が移行している(ムーブ)しているため、移行後にs1を利用することはできない。
```rust
let s1 = String::from("hello");
let s2 = s1;

println!("{}, world!", s1); //ここでs1は利用できない

// cloneでdeep copyすればOK
let s1 = String::from("hello");
let s2 = s1.clone();

println!("s1 = {}, s2 = {}", s1, s2);
```

関数の引数として渡す場合も所有権が移行する。
```&```をつけて参照を渡すと所有権を移行させずにすむ。
※関数の引数に参照を取ることを「借用」という。
```rust
let s1 = String::from("test");
let s2 = calculate_length1(s1);
println!("{}", s2);
println!("{}", s1); // s1はs2にムーブしてるためコンパイルエラーとなる

let s3 = String::from("test");
let s4 = calculate_length2(&s3);
println!("{}", s4);
println!("{}", s3); // 参照を渡しておりムーブしていないのでコンパイルエラーとならない

fn calculate_length1(s: String) -> usize {
    s.len()
}

// 参照を取る(ムーブしない)
fn calculate_length2(s: &String) -> usize {
    s.len()
    // s.push_str("aaa") など参照は書き換えることはできない
}
```
