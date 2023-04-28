# 第2课 课后作业

## 第1题 转换为bit位 Num2Bits

```circom
pragma circom 2.1.4;

template Num2Bits (nBits) {
    signal input in;

    signal output b[nBits];
    
    var acc = 0;
    for (var i = 0; i < nBits; i++) {
        b[i] <-- (in \ 2 ** i) % 2;
        0 === b[i] * (b[i] - 1);
        acc += b[i] * 2 ** i;
    }
    in === acc;

}

template Main () {
    signal input in;
    signal output out[5];
    component n2b = Num2Bits(5);
    n2b.in <== in;
    out <== n2b.b;
}

component main = Main();

/* INPUT = {
    "in": "11"
} */
```

## 第2题 判零 IsZero

```circom
pragma circom 2.1.4;

template IsZero() {
    signal input in;
    signal output out;
    signal inv;
    inv <-- in!=0 ? 1/in : 0;
    out <== -in*inv +1;
    in*out === 0;
}

template Main () {
    signal input in;
    signal output out;
    component iszero = IsZero();
    iszero.in <== in;
    out <== iszero.out;
}

component main = Main();

/* INPUT = {
    "in": "12"
} */
```

## 第3题 相等 IsEqual

```circom
pragma circom 2.1.4;

template IsZero() {
    signal input in;
    signal output out;
    signal inv;
    inv <-- in!=0 ? 1/in : 0;
    out <== -in*inv +1;
    in*out === 0;
}

template IsEqual() {
    signal input in[2];
    signal output out;
    component iszero = IsZero();
    iszero.in <== in[0] - in[1];
    out <== iszero.out;
}

template Main () {
    signal input in[2];
    signal output out;
    component isequal = IsEqual();
    isequal.in <== in;
    out <== isequal.out;
}

component main = Main();

/* INPUT = {
    "in": ["3","3"]
} */
```

## 第4题 选择器 Selector

```circom

```

## 第5题 判负 IsNegative

```circom

```

## 第6题 少于 LessThan

```circom

```

## 第7题 整数除法 IntegerDivide

```circom

```
