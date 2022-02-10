---
title: Expression Language
tags:
  - programming
  - lang
  - el
categories:
  - programming
  - java
date: 2022-02-09 13:29:45
---

# Expression Language



## Literal Expressions

A literal expression is evaluated to the text of the expression, which is of type `String`. A literal expression does not use the `${}` or `#{}` delimiters.

If you have a literal expression that includes the reserved `${}` or `#{}` syntax, you need to escape these characters as follows:

- By creating a composite expression as shown here:

  ```
  ${'${'}exprA}
  ```

  ```
  #{'#{'}exprB}
  ```

  The resulting values would then be the strings `${exprA}` and `#{exprB}`.

- By using the escape characters `\$` and `\#` to escape what would otherwise be treated as an eval-expression:

  ```
  \${exprA}
  ```

  ```
  \#{exprB}
  ```

  The resulting values would again be the strings `${exprA}` and `#{exprB}`.

When a literal expression is evaluated, it can be converted to another type. [Table 6-2](https://docs.oracle.com/javaee/6/tutorial/doc/bnaid.html#bnaie) shows examples of various literal expressions and their expected types and resulting values.



Table 6-2 Literal Expressions

| Expression | Expected Type | Result         |
| ---------- | ------------- | -------------- |
| `Hi`       | `String`      | `Hi`           |
| `true`     | `Boolean`     | `Boolean.TRUE` |
| `42`       | `int`         | `42`           |

Literal expressions can be evaluated immediately or deferred and can be either value or method expressions. At what point a literal expression is evaluated depends on where it is being used. If the tag attribute that uses the literal expression is defined to accept a deferred value expression, when referencing a value, the literal expression is evaluated at a point in the lifecycle that is determined by other factors, such as where the expression is being used and to what it is referring.

In the case of a method expression, the method that is referenced is invoked and returns the specified `String` literal. For example, the `h:commandButton` tag of the `guessnumber` application uses a literal method expression as a logical outcome to tell the JavaServer Faces navigation system which page to display next.

## Operators

In addition to the `.` and `[]` operators discussed in [Value and Method Expressions](https://docs.oracle.com/javaee/6/tutorial/doc/bnahu.html), the EL provides the following operators, which can be used in rvalue expressions only:

- **Arithmetic**: `+`, `-` (binary), `*`, `/` and `div`, `%` and `mod`, `-` (unary)
- **Logical**: `and`, `&&`, `or`, `||`, `not`, `!`
- **Relational**: `==`, `eq`, `!=`, `ne`, `<`, `lt`, `>`, `gt`, `<=`, `ge`, `>=`, `le`. Comparisons can be made against other values or against Boolean, string, integer, or floating-point literals.
- **Empty**: The `empty` operator is a prefix operation that can be used to determine whether a value is `null` or empty.
- **Conditional**: `A ? B : C`. Evaluate `B` or `C`, depending on the result of the evaluation of `A`.

The precedence of operators highest to lowest, left to right is as follows:

- `[] .`
- `()` (used to change the precedence of operators)
- `-` (unary) `not ! empty`
- `* / div % mod`
- `+ -` (binary)
- `< > <= >= lt gt le ge`
- `== != eq ne`
- `&& and`
- `|| or`
- `? :`

## Examples of EL Expressions

[Table 6-3](https://docs.oracle.com/javaee/6/tutorial/doc/bnaim.html#bnain) contains example EL expressions and the result of evaluating them.

Table 6-3 Example Expressions

| EL Expression                                           | Result                                                       |
| ------------------------------------------------------- | ------------------------------------------------------------ |
| `${1 > (4/2)}`                                          | `false`                                                      |
| `${4.0 >= 3}`                                           | `true`                                                       |
| `${100.0 == 100}`                                       | `true`                                                       |
| `${(10*10) ne 100}`                                     | `false`                                                      |
| `${'a' < 'b'}`                                          | `true`                                                       |
| `${'hip' gt 'hit'}`                                     | `false`                                                      |
| `${4 > 3}`                                              | `true`                                                       |
| `${1.2E4 + 1.4}`                                        | `12001.4`                                                    |
| `${3 div 4}`                                            | `0.75`                                                       |
| `${10 mod 4}`                                           | `2`                                                          |
| `${!empty param.Add}`                                   | `False` if the request parameter named `Add` is `null` or an empty string. |
| `${pageContext.request.contextPath}`                    | The context path.                                            |
| `${sessionScope.cart.numberOfItems}`                    | The value of the `numberOfItems` property of the session-scoped attribute named `cart`. |
| `${param['mycom.productId']}`                           | The value of the request parameter named `mycom.productId`.  |
| `${header["host"]}`                                     | The host.                                                    |
| `${departments[deptName]}`                              | The value of the entry named `deptName` in the `departments` map. |
| `${requestScope['javax.servlet.forward.servlet_path']}` | The value of the request-scoped attribute named `javax.servlet.forward.servlet_path`. |
| `#{customer.lName}`                                     | Gets the value of the property `lName` from the `customer` bean during an initial request. Sets the value of `lName` during a postback. |
| `#{customer.calcTotal}`                                 | The return value of the method `calcTotal` of the `customer` bean. |

## 参考

[The Java EE 6 Tutorial Expression Language](https://docs.oracle.com/javaee/6/tutorial/doc/gjddd.html)

[**JSR 341: Expression Language 3.0**](https://download.oracle.com/otn-pub/jcp/el-3_0-fr-eval-spec/EL3.0.FR.pdf?AuthParam=1644385241_a437ff66c3ee49489355d01cfcb7fc70)

