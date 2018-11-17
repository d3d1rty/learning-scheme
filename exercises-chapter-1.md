# Exercise 1.1
Below is a sequence of expressions. What is the result printed by the interpreter in response to each expression? Assume that the sequence is to be evaluated in
the order in which it is presented.

`10`

~Answer~: Prints 10.

`(+ 5 3 4)`

~Answer~: Adds all values and prints sum (12) to the screen.

`(- 9 1)`

~Answer~: Subtracts 1 from 9 and prints remainder (8) to the screen.

`(/ 6 2)`

~Answer~: Divides 6 by 2 and prints result (3) to the screen.

`(+ (* 2 4) (- 4 6))`

~Answer~: Multiplies 2 and 4 (8), subtracts 6 from 4 (-2), and then adds the result of both expressions (6) and prints to the screen.

`(define a 3)`

~Answer~: Associates the value 3 with the symbol a.

`(define b (+ a 1))`

~Answer~: Associates the result of the expression a + 1 with the symbol b.

`(+ a b (* a b))`

~Answer~: Multiplies a and b, and then adds a b and the product of the previously evaluated expression, printing result to the screen (19).

`(= a b)`

~Answer~: Compares a and b to determine if equal, returns false.

```
(if (and (> b a) (< b (* a b)))
 b
 a)
```

~Answer~: First, multiplies a and b (12) and then determines if b is less than that product (true). Then, determines if b is greater than a (true) and returns true only if
both statements (b less than product of a and b; b less than a) are true (true). Returns value of b (4) since both statements are true.

```
(cond ((= a 4) 6)
 ((= b 4) (+ 6 7 a))
 (else 25))
```

~Answer~: If a is equal to 4 (false), return 6. Else if b is equal to 4 (true), return the sum of 6, 7, and a (16). Else return 25. The conditional statement returns 16.

`(+ 2 (if (> b a) b a))`

~Answer~: If b is greater than a (true), return b; else return a. Then, add two to the value returned (6).

```
(* (cond ((> a b) a)
    ((< a b) b)
    (else -1))
 (+ a 1))
```

~Answer~: If a is greater than b (false), return a; else if a is less than b (true), return b; else, return -1. Then, add the value of a and 1 (4). Multiply the value returned
from the conditional (4) by the sum of a and 1 (4). Print result to screen (16).

# Exercise 1.2
Translate the following expression into prefix form:

```
5 + 4 + (2 − (3 − (6 + 5/4 )))
------------------------------
3(6 − 2)(2 − 7)
```

~Answer~: Translated to prefix form:
```
(/ (+ 5 4 (- 2 3 (+ 6 (/ 5 4))))
 (* 3 (- 6 2)(- 2 7)))
```

# Exercise 1.3
Define a procedure that takes three numbers as arguments and returns the sum of the squares of the two larger numbers.

~Answer~:
```
(define (sum-of-squares-variant a b c)
 (cond ((or (and (> a b)(> b c))(and (> b a)(> a c))) (+ (* a a)(* b b)))
       ((or (and (> b c)(> c a))(and (> c b)(> b a))) (+ (* b b)(* c c)))
       ((or (and (> c a)(> a b))(and (> a c)(> c b))) (+ (* a a)(* c c)))))
```

# Exercise 1.4
Observe that our model of evaluation allows for combinations whose operators are compound expressions. Use this observation to describe the behavior of the
following procedure:

```
(define (a-plus-abs-b a b)
 ((if (> b 0) + -) a b))
```

~Answer~: The function takes two parameters (a and b). If b is greater than 0, the conditional returns the + operator; else, it returns the - operator. The operator returned
then forms the expression to evaluate the a and b values remaining.

# Exercise 1.5
Ben Bitdiddle has invented a test to determine whether the interpreter he is faced with is using applicative-order evaluation or normal-order evaluation.
He defines the following two procedures:

```
(define (p) (p))
(define (test x y)
 (if (= x 0) 0 y))
```

Then he evaluates the expression:
`(test 0 (p))`

What behavior will Ben observe with an interpreter that uses applicative-order evaluation? What behavior will he observe with an interpreter that uses normal-order
evaluation? Explain your answer. (Assume that the evaluation rule for the special form if is the same whether the interpreter is using normal or applicative order:
The predicate expression is evaluated first, and the result determines whether to evaluate the consequent or the alternative expression.)

~Answer~: Applicative-order would result in the procedure p looping continuously, thus never terminating.
