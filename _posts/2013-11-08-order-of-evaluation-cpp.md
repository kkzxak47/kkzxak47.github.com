---
layout: post
title: "Cpp - Order of Evaluation"
description: ""
category: "cpp"
tags: []
---
{% include JB/setup %}
## from C++ Primer, Fifth Edition, page 193
4.1.3. Order of Evaluation
 
Precedence specifies how the operands are grouped. It says nothing about the order
in which the operands are evaluated. In most cases, the order is largely unspecified.
In the following expression
 
    int i = f1() * f2();
 
we know that f1 and f2 must be called before the multiplication can be done. After
all, it is their results that are multiplied. However, we have no way of knowing
whether f1 will be called before f2 or vice versa.
 
For operators that do not specify evaluation order, it is an error for an expression to
refer to and change the same object. Expressions that do so have undefined behavior
(chap 2.1.2, p. 36). As a simple example, the << operator makes no guarantees about
when or how its operands are evaluated. As a result, the following output expression
is undefined:
 
Click here to view code image
 
    int i = 0;
    cout << i << " " << ++i << endl; // undefined
 
Because this program is undefined, we cannot draw any conclusions about how it
might behave. The compiler might evaluate ++i before evaluating i, in which case
the output will be 1 1. Or the compiler might evaluate i first, in which case the
output will be 0 1. 
Or the compiler might do something else entirely.
 Because this expression has undefined behavior, the program is in error, regardless of what code
the compiler generates.
 
There are four operators that do guarantee the order in which operands are
evaluated. We saw in chap 3.2.3 (p. 94) that the logical AND (&&) operator guarantees
that its left-hand operand is evaluated first. Moreover, we are also guaranteed that the
right-hand operand is evaluated only if the left-hand operand is true. The only other
operators that guarantee the order in which operands are evaluated are the logical OR
(||) operator (chap 4.3, p. 141), the conditional (? :) operator (chap 4.7, p. 151), and the
comma (,) operator (chap 4.10, p. 157).
 
Order of Evaluation, Precedence, and Associativity
 
Order of operand evaluation is independent of precedence and associativity. In an
expression such as f() + g() * h() + j():
 
• Precedence guarantees that the results of g() and h() are multiplied.
 
• Associativity guarantees that the result of f() is added to the product of g()C++ Primer, Fifth Edition
and h() and that the result of that addition is added to the value of j().
 
• There are no guarantees as to the order in which these functions are called.
 
If f, g, h, and j are independent functions that do not affect the state of the same
objects or perform IO, then the order in which the functions are called is irrelevant. If
any of these functions do affect the same object, then the expression is in error and
has undefined behavior.
 
Exercises Section 4.1.3
 
Exercise 4.3:  Order  of  evaluation  for  most  of  the  binary  operators  is left
undefined  to  give  the  compiler  opportunities  for  optimization.  This strategy
presents a trade-off between efficient code generation and potential pitfalls in
the  use  of  the  language  by  the  programmer.  Do  you  consider  that  an
acceptable trade-off? Why or why not?
 
 
Advice: Managing Compound Expressions
 
When you write compound expressions, two rules of thumb can be helpful:
 
1. When in doubt, parenthesize expressions to force the grouping that the
logic of your program requires.
 
2. If you change the value of an operand, don't use that operand elsewhere
in the same expresion.
 
An important exception to the second rule occurs when the subexpression
that changes the operand is itself the operand of another subexpression. For
example, in *++iter, the increment changes the value of iter. The (now
changed) value of iter is the operand to the dereference operator. In this
(and similar) expressions, order of evaluation isn't an issue. The increment
(i.e., the subexpression that changes the operand) must be evaluated before
the dereference can be evaluated. Such usage poses no problems and is
quite common.
