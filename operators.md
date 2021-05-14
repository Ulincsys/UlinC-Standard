# Standard Operators

An *operator* is a symbol or group of symbols which perform a pre-defined action on one or more Objects. UlinC supports [infinitary operators](https://en.wikipedia.org/wiki/Finitary) (meaning that one operator can have any number of operands). All standard UlinC operators have a minimum [arity](https://en.wikipedia.org/wiki/Arity) of at least 1, which are referred to as **Unary Operators** when used in this way. Operators which have a minimum arity of 2 are called **Binary Operators** when used in this way. Unless otherwise stated, the resulting type of all operations is preferential to the leftmost type in the expression.

An *expression* is any statement which utilizes an operator. If a statement contains more than one operator, that statement contains a number of expressions equal to the number of operators.

The UlinC language standard provides many operators.

***

| Symbol  | Basic Syntax | Operator Name | Operator Description |
| :-----: | :----: |------------- | -------------------- |
| **+** | `a + {b}` | Addition  | Add two or more operands |
| **-** | `a - {b}` | Subtraction  | Subtract two or more operands |
| **\*** | `a * {b}` | Multiplication | Multiply two or more operands |
| **/** | `a / {b}` | Division | Divide two or more operands |
| **=** | `{a} = b` | Assignment | Set one or more operands comparatively equal to a statement |
| **==** | `{a} == b` | Equality | Determine if one or more operands are comparatively equal to a statement |
| **?:** | `a ? b : c` | Inline If | Branch on the truth of a statement |
| **<=>** | `a <=> b` | Triple Compare | Three-way comparison between two operands, evaluates to -1 if `a < b`, 0 if `a == b`, else 1 |

***

## Infinitary Operators

*Infinitary operators* (denoted in the operators table by operands surrounded with braces) work with a functionally limitless number of operands. Syntactically, the operands are provided in braces and separated by commas. For example;

_A + {X<sub>1</sub>, X<sub>2</sub>, X<sub>3</sub>, ... X<sub>n</sub>};_

evaluates to;

_A + X<sub>1</sub> + X<sub>2</sub> + X<sub>3</sub> + ... X<sub>n</sub>;_

## Expression Precedence

All expressions have a defined _precedence_ used to determine in which order they are evaluated. UlinC generally executes expressions in the following order:
* Left-most
  * Any statements of equal precedence will be evaluated from left-to-right
* Parentheses, Braces, Brackets
  * Any statements within an expression enclosed with parentheses, braces, or brackets will be evaluated before the rest of the expression, starting first with the innermost pair
* Multiplication and Division
  * Any operations involving Multiplication and Division will be evaluated after all relevant statements within parentheses have been evaluated. Multiplication and Division have the same precedence
* Addition and Subtraction
  * Any operations involving Addition and Subtraction will be evaluated after all relevant statements involving Multiplication and Division have been evaluated. Addition and Subtraction have the same precedence

## User Defined Operators

UlinC provides users with the ability to define custom operators (also referred to as [Operator Overloading](https://en.wikipedia.org/wiki/Operator_overloading)), which can be implemented once per operator/operands combination. User defined operators are not required to be defined in terms of existing operators, but they **must not** interfere with any reserved words or program symbols. It is recommended that user defined operators be comprised of some combination of standard operator symbols.

Operator definitions can be made anywhere within the Global Scope, but conventionally they are defined within the type which is the leftmost operand of the operation.