# [Simple statement](https://docs.python.org/3/reference/simple_stmts.html#assert)
A simple statement is comprised with a single logical line, Several simple statements may occur on a single line sperated by semicolons.
The syntax for simple statement is:
```
simple_stmt ::=  expression_stmt
                 | assert_stmt
                 | assignment_stmt
                 | augmented_assignment_stmt
                 | annotated_assignment_stmt
                 | pass_stmt
                 | del_stmt
                 | return_stmt
                 | yield_stmt
                 | raise_stmt
                 | break_stmt
                 | continue_stmt
                 | import_stmt
                 | global_stmt
                 | nonlocal_stmt

```


## The assert statement
Assert statements are a convenient way to insert debugging assertions into a program
```
assert_stmt ::=  "assert" expression ["," expression]
```
The sample form, *assert expression*, is equivalent to
```
if __debug__:
   if not expression raise AssertionError
```
The extended form, *assert expression1, expression2* is equivalent to
```
if __debug__:
   if not expression1 raise AssertionError(expression2)
```
```
assert True
assert False     # AssertionError
assert(2 + 2 == 5, "Houston we've got a problem")  # bool((False,)) = False, (False,) is not empty
<string>:1: SyntaxWarning: assertion is always true, perhaps remove parentheses?
SyntaxWarning: assertion is always true, perhaps remove parentheses?

assert 2 + 2 == 5, "Houston we've got a problem"
AssertionError: Houston we've got a problem
```
