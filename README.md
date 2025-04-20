# COMPILER-DESIGN-BASICS
COMPANY: CODTECH IT SOLUTIONS

NAME: KUNALI BHAVARTHE

INTERN ID: CT2MTXEI

DOMAIN: C++ PROGRAMMING

DURATION: 8 WEEEKS

MENTOR: NEELA SANTHOSH

Theory and Description of the C++ Program for Evaluating Arithmetic Expressions
This C++ program implements an expression evaluator that parses and evaluates arithmetic expressions containing basic operators (addition, subtraction, multiplication, and division), along with parentheses for controlling operator precedence.

Let's break down the theory and description of the core concepts and the approach used in this program:

1. Expression Evaluation
In mathematics, arithmetic expressions follow a well-defined order of operations. The common rules are:

Parentheses () take the highest precedence.

Multiplication * and Division / have a higher precedence than Addition + and Subtraction -.

Addition and Subtraction have the lowest precedence among these operators.

The goal of this program is to take an arithmetic expression (in infix notation, which is the usual way we write expressions like 3 + 5 * 2) and evaluate it according to the order of operations.

2. Stacks for Expression Evaluation
To solve the problem of evaluating expressions correctly, the program uses two stacks:

A stack for operands: This stack holds the numbers as the expression is processed.

A stack for operators: This stack holds operators (+, -, *, /) and parentheses as they appear in the expression.

3. Algorithm Overview
The algorithm uses the following steps to evaluate the expression:

Step 1: Process Each Character in the Expression

If the character is a number: Convert it to an integer (it could be multiple digits) and push it onto the operand stack.

If the character is an operator (+, -, *, /):

Check the precedence of the current operator against the operator on top of the operator stack.

If the top operator in the stack has higher or equal precedence, apply the operation between the top two operands from the operand stack and pop the operator from the operator stack. Repeat this until the stack is empty or a lower precedence operator is found.

Push the current operator onto the operator stack.

If the character is an opening parenthesis (: Push it onto the operator stack.

If the character is a closing parenthesis ): Pop operators from the operator stack and apply them to operands until an opening parenthesis ( is encountered. Discard the opening parenthesis.

Step 2: Apply Remaining Operators After processing all characters in the expression, any remaining operators in the stack are applied to the operands in the stack.

Step 3: Return the Result The final result is the single value left in the operand stack after all operations have been performed.

4. Operator Precedence and Associativity
The program uses the precedence function to determine the precedence of operators:

Operators * and / have higher precedence (2).

Operators + and - have lower precedence (1).

The applyOperation function performs the arithmetic operations based on the current operator, and ensures that division by zero is handled safely.

5. Handling Parentheses
Parentheses in arithmetic expressions allow us to explicitly change the natural order of operations. The program handles parentheses by ensuring that any expression inside parentheses is evaluated first. When encountering a closing parenthesis ), the program evaluates the expression inside the parentheses by popping operators from the stack and applying them to the operands.

6. Evaluation Example:
For the expression (3 + 5) * 2 - 4 / 2, the program proceeds as follows:

First, it handles the parentheses (3 + 5) and pushes the result 8 onto the operand stack.

Then it multiplies 8 by 2, yielding 16.

Finally, it divides 4 by 2, yielding 2, and subtracts 2 from 16, yielding the final result 12.

7. Edge Cases Handled
Parentheses: The program correctly handles nested and multiple parentheses.

Division by Zero: The program raises an error if a division by zero is attempted.

Multiple-Digit Numbers: The program can handle multi-digit numbers, not just single digits.

Conclusion
The C++ program demonstrates how to evaluate mathematical expressions by simulating the traditional manual approach of operator precedence using two stacks. The use of stacks ensures that operations are applied in the correct order and allows the program to handle complex expressions, including those with parentheses and various operators. This approach follows a classic shunting yard algorithm (or Dijkstra's algorithm) for parsing expressions.
