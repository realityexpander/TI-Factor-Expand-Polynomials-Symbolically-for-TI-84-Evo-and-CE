# `FACTOR` and `EXPAND` Polynomials Symbolically 
## For TI-84 Evo & CE/Plus-CE Calculators

<img width="324" height="244" alt="image" src="https://github.com/user-attachments/assets/4692e3d8-ed55-4a53-ab7e-8e84b51b9b7f" />

TI-BASIC calculator programs that provide lightweight polynomial factoring and expansion using computer-algebra-style expression strings. Useful for performing coursework in college level algebra, pre-calculus, calculus 1 & 2. Provides some CAS level functionality for non-CAS calculators that are allowed to be used in these courses to check your work.

The repository contains two standalone programs for both TI-84 Evo and CE/Plus-CE calculators:

* **`FACTOR`** — factors an expanded polynomial expression.
* **`EXPAND`** — expands products and powers of polynomial factors.

Both programs receive their input as a **standard computer algebra formatted string stored in `Ans`** and returns the result as a computer algebra formatted string in `Ans`.

These programs are intended to provide convenient polynomial manipulation on the TI-84 Evo without requiring a CAS calculator.

<h2>To Install on TI-84 Evo:</h2>

use the `.8xp2` files

Online Calculator
  - [https://ti84evo.ti.com/84evo/en/main-view](https://ti84evo.ti.com/84evo/en/main-view)
  - Use "Send Files" - "send to calculator" to send a program file on computer to a the emulator calculator.
  - Use "Send Files" - "send to computer" to copy a program from the emulator calculator to your computer files.

Connect to Physical Calculator
  - [https://connectevo.ti.com/ticevo/en/main-view](https://connectevo.ti.com/ticevo/en/main-view)
  - Use "send to calculator" to send a program file to a physically connected calculator.
  - Use "send to computer" to copy a program from the physical connected calculator to your computer files.

<h2>To Install on TI-84 CE/Plus CE:</h2>

use the `.8xp` files

Online Calculator (login realityexpander)
  - [https://ti84evo.ti.com/84evo/en/main-view](https://84plusce.ti.com/8eu/main-view)

Connect to Physical Calculator
  - Use "TI Connect CE" App
  - Use "send to calculator" to send a program file to a physically connected calculator.
  - Use "send to computer" to copy a program from the physical connected calculator to your computer files.

  - Web-based Alternative to "TI Connect CE"
    - https://ticalc.link/  

# General Program Functionality

## `FACTOR` Program

`FACTOR` accepts an expanded polynomial such as:

```text
6*X^3+33*X^2-81*X-378
```

and factors it into:

```text
3*(2*X-7)*(X+3)*(X+6)
```

Mathematically:

$$6x^3+33x^2-81x-378$$

becomes:

$$3(2x-7)(x+3)(x+6)$$

The `FACTOR` program:

* Uses the expression string stored in `Ans` and parses it as a polynomial expression.
* Converts the expression into polynomial coefficients.
* Extracts the greatest common integer factor of the coefficients.
* Detects factors of (x).
* Searches for integer roots.
* Uses synthetic division to remove discovered factors.
* Detects repeated factors.
* Returns the remaining polynomial factor when it cannot be reduced further.
* Produces a computer algebra formatted result string.

[How to use `FACTOR` program](#how-to-use-factor)

---

## `EXPAND` Program

`EXPAND` performs the reverse operation of `FACTOR`

For example:

```text
3*(2*X-7)*(X+3)*(X+6)
```

is expanded to:

```text
6*X^(3)+33*X^(2)-81*X-378
```

Mathematically:

$$3(2x-7)(x+3)(x+6)$$

becomes:

$$6x^3+33x^2-81x-378$$

The program:

* Uses the expression string stored in `Ans` and parses it as a polynomial expression.
* Recognizes parenthesized factors.
* Recognizes repeated factors such as `(X+2)^2`.
* Converts each factor into a coefficient list.
* Multiplies polynomials using coefficient convolution.
* Combines like terms.
* Returns the expanded polynomial as a computer algebra formatted string.

[How to use `EXPAND` program](#how-to-use-expand)

---

# Intended Use

These programs are designed for polynomial problems commonly encountered in:

* Algebra 1 & 2
* College Algebra
* Precalculus
* Calculus I
* Calculus II

They are especially useful for checking algebra involved in:

* Polynomial equations
* Factoring
* Expanding products
* Simplifying expressions
* Rational-function preparation
* Limits
* Derivatives
* Integrals
* Partial-fraction decompositon preparation

The goal is **NOT** to reproduce a complete CAS system. Instead, the programs provide focused polynomial functionality appropriate for standard undergraduate mathematics coursework using integer polynomial coefficients and constants.

---

# Known Limitations

These programs intentionally support a limited subset of computer algebra syntax that is found in standard high school and undergraduate math courses.

## `FACTOR` limitations

`FACTOR` is intended primarily for **integer-coefficient polynomials and real algebraic factoring**.

It does not attempt to return complex factors.

For example, an irreducible factor such as:

$$x^2+1$$

is left as:

```text
X^(2)+1
```

rather than being converted into complex factors involving (i).

The program is intended for the kinds of polynomial factors normally encountered in Algebra, Precalculus, Calculus I, and Calculus II coursework.

Additional limitations:

* One polynomial variable only: `X`
* Integer polynomial exponents
* Nonnegative exponents only
* Intended primarily for integer coefficients
* Does not function as a general-purpose symbolic algebra system
* Does not factor expressions involving functions such as `sin`, `cos`, `ln`, or `sqrt`
* Does not factor rational expressions containing polynomial denominators
* Does not return complex roots
* Does not attempt arbitrary symbolic radical factorization

An expression that cannot be further factored using the supported methods is returned as a remaining polynomial factor.

---

## `EXPAND` limitations

`EXPAND` is designed for ordinary polynomial products.

Supported examples include:

```text
(X+2)*(X-3)
```

```text
(X+2)^2
```

```text
3*(2*X-7)*(X+3)*(X+6)
```

It is not intended to expand general symbolic expressions involving:

```text
sin(X)
cos(X)
ln(X)
sqrt(X)
1/(X+1)
X^(-2)
X^(1/2)
```

The program assumes:

* One variable: `X`
* Nonnegative integer powers
* Polynomial factors
* Standard computer algebra style input

---

# Computer Algebra Input Format

Uppercase `X` is recommended.

Examples of valid polynomial syntax:

```text
X^2+X-6
```

```text
3*X^3-5*X+2
```

```text
(X+2)*(X-3)
```

```text
(X+2)^2
```

```text
(X+2)^(2)
```

```text
3*(2*X-7)*(X+3)*(X+6)
```

Both forms:

```text
X^2
```

and:

```text
X^(2)
```

are supported where appropriate.

---

# How to Use `FACTOR`

Enter the polynomial as a quoted string:

```text
"X^2+X-6"
```

Press **ENTER**.

The string is now stored in `Ans`.

Run:

```text
prgmFACTOR
```

The program displays:

```text
(X-2)*(X+3)
```

The resulting string is also left in `Ans`.

---

# `FACTOR` Examples

## Example 1 — Simple Difference of Squares

### Input

Mathematically:

$$x^2-9$$

Computer algebra string:

```text
"X^2-9"
```

Run:

```text
prgmFACTOR
```

### Output

Mathematically:

$$(x-3)(x+3)$$

Computer algebra format:

```text
(X-3)*(X+3)
```

---

## Example 2 — Quadratic Trinomial

### Input

Mathematically:

$$x^2+x-6$$

Computer algebra string:

```text
"X^2+X-6"
```

Run:

```text
prgmFACTOR
```

### Output

Mathematically:

$$(x-2)(x+3)$$

Computer algebra format:

```text
(X-2)*(X+3)
```

---

## Example 3 — Cubic With a Common Coefficient

### Input

Mathematically:

$$6x^3+33x^2-81x-378$$

Computer algebra string:

```text
"6*X^3+33*X^2-81*X-378"
```

Run:

```text
prgmFACTOR
```

### Output

Mathematically:

$$3(2x-7)(x+3)(x+6)$$

Computer algebra format:

```text
3*(2*X-7)*(X+3)*(X+6)
```

The order of equivalent factors may vary without changing the mathematical result.

---

# How to Use `EXPAND`

Enter the factored polynomial as a quoted string:

```text
"(X+2)*(X-3)"
```

Press **ENTER**.

The string is now stored in `Ans`.

Run:

```text
prgmEXPAND
```

The expanded polynomial is displayed and left in `Ans`.

---

# `EXPAND` Examples

## Example 1 — Two Linear Factors

### Input

Mathematically:

$$(x+2)(x-3)$$

Computer algebra string:

```text
"(X+2)*(X-3)"
```

Run:

```text
prgmEXPAND
```

### Output

Mathematically:

$$x^2-x-6$$

Computer algebra format:

```text
X^(2)-X-6
```

---

## Example 2 — Repeated Factor

### Input

Mathematically:

$$(x+2)^2(x-1)$$

Computer algebra string:

```text
"(X+2)^2*(X-1)"
```

Run:

```text
prgmEXPAND
```

### Output

Mathematically:

$$x^3+3x^2-4$$

Computer algebra format:

```text
X^(3)+3*X^(2)-4
```

---

## Example 3 — Multiple Factors and Scalar Coefficient

### Input

Mathematically:

$$3(2x-7)(x+3)(x+6)$$

Computer algebra string:

```text
"3*(2*X-7)*(X+3)*(X+6)"
```

Run:

```text
prgmEXPAND
```

### Output

Mathematically:

$$6x^3+33x^2-81x-378$$

Computer algebra format:

```text
6*X^(3)+33*X^(2)-81*X-378
```

---

# Using `FACTOR` and `EXPAND` Together

Because both programs accept and return computer algebra formatted strings, they can be used together.

For example:

```text
"X^2+X-6"
```

Run:

```text
prgmFACTOR
```

Result:

```text
(X-2)*(X+3)
```

Then immediately run:

```text
prgmEXPAND
```

Result:

```text
X^(2)+X-6
```

Mathematically:

$$x^2+x-6$$

$$\downarrow\ \text{FACTOR}$$

$$(x-2)(x+3)$$

$$\downarrow\ \text{EXPAND}$$

$$x^2+x-6$$

This makes the programs useful both for performing polynomial operations and for checking algebraic work on the TI-84 Evo.

---

# Project Scope

`FACTOR` and `EXPAND` are intentionally focused programs rather than replacements for a CAS calculator.

Their purpose is to provide useful polynomial factoring and expansion capabilities for the TI-84 Evo within the scope of ordinary Algebra through Calculus II coursework, while keeping the implementation entirely in TI-BASIC.
