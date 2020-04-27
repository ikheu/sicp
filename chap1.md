### 1.1 命令行求值 p13
```scheme
> 10
10
> (+ 5 4 3)
12
> (- 9 1)
8
> (/ 6 2)
3
> (+ (* 2 4) (- 4 6))
6
> (define a 3)
> (define b (+ a 1))
> (+ a b (* a b))
19
> (= a b)
#f
> (if (and (> b a) (< b (* a b)))
      b
      a)
4
> (cond ((= a 4) 6)
        ((= b 4) (+ 6 7 a))
        (else 25)
        )
16
> (+ 2 (if (> b a) b a))
6
> (* (cond ((> a b) a)
           ((< a b) b)
           (else -1))
     (+ a 1))
16
```
---
### 1.2 前缀表达式 p13
```scheme
(/ (+ 5 4
        (- 2 (- 3 (+ 6 (/ 4 5)))))
     (* 3 (- 6 2) (- 2 7)))
```
---
### 1.3 三个数的最大值 p13
```scheme
(define (max a b)
  (if (> a b) a b))

(define (max3 a b c)
  (max (max a b) c))
```

---
### 1.4 描述过程的行为 p13
`a + abs(b)`

---
### 1.5 正则序与应用序 p13
过程 p 调用自身。对于应用序求值，不糊看到结果。对于正则序求值，结果为 10。

---
### 1.6 if 新版本存在的问题 p16
sqrt-iter 会不断被调用求值，导致程序无法终止。

---
### 1.7 计算终止条件 good-enought 的改进 p16

---
### 1.8 立方根过程
```scheme
(define eps 0.000000001)

(define (abs x) (if (< x 0) (- x) x))

(define( good-enought y x)
  (< (abs (- (* y y y) x)) eps))

(define (cube-iter y x)
  (if (good-enought y x)
      y
      (cube-iter (cube-improve y x) x)))

(define (cube-improve y x)
  (/ (+ (/ x (* y y )) (* 2 y)) 3))

(define (cube-root x)
  (cube-iter 1 x))
```



