# MAT1252 Exam Cheatsheet
*Covers Modules 1–5: Number bases · Symbolic logic · Boolean algebra · Karnaugh maps · Predicates & sets*

---

## MODULE 1 — Number bases & representation

### 1.1 Bases & subscripts
- Subscripts identify the base: $354_{10}$ (dec), $354_8$ (oct), $1010_2$ (bin), $A3F_{16}$ (hex).
- Positional notation: every digit's value = digit × base^position.

| Base | Digits used | Common name |
|------|-------------|-------------|
| 2  | 0–1 | binary |
| 8  | 0–7 | octal |
| 10 | 0–9 | decimal |
| 16 | 0–9, A=10, B=11, C=12, D=13, E=14, F=15 | hexadecimal |

### 1.2 Powers you must memorise
- Powers of 2: 1, 2, 4, 8, 16, 32, 64, 128, 256, 512, 1024.
- Powers of 8: 1, 8, 64, 512, 4096.
- Powers of 16: 1, 16, 256, 4096, 65536.

### 1.3 Conversions to decimal (**Summation**)
Expand using base-powers, then add.
- $213_8 = 2(64)+1(8)+3 = 139_{10}$
- $1011_2 = 8+0+2+1 = 11_{10}$
- $5C_{16} = 5(16)+12 = 92_{10}$

### 1.4 Decimal → other base (**Repeated division**)
Divide by the base; read remainders **bottom-up**.
- $171_{10} \to 8$: 171/8=21 r3, 21/8=2 r5, 2/8=0 r2  ⇒ $253_8$.
- $58_{10} \to 2$: gives remainders 0,1,0,1,1,1 ⇒ $111010_2$.

### 1.5 Binary ↔ Octal (group of **3**)
Group binary bits in 3s **from the right**, replace each group with octal digit (or vice-versa).
- $10111001_2 = 10\,111\,001 = 271_8$.

### 1.6 Binary ↔ Hex (group of **4**)
Group bits in 4s from right, replace with hex digit.
- $10111011001_2 = 101\,1101\,1001 = 5D9_{16}$.

### 1.7 Octal ↔ Hex (via binary)
Convert via binary as a bridge.

### 1.8 Binary fractions
Columns after the point = $\tfrac{1}{2}, \tfrac{1}{4}, \tfrac{1}{8}, \dots$
- **Binary fraction → decimal**: read integer after point, divide by $2^k$ (k = # places).
  - $0.110011_2$: $110011_2=51$, k=6 → $51/64 = 0.78125$… (use $51/64=0.796875$)
- **Decimal fraction → binary**: repeatedly multiply by 2, read integer parts top-down, until 0.
  - $0.34375 \to 0.01011_2$.

### 1.9 Arithmetic
**Addition rule**: a carry of 1 occurs when the column sum ≥ the base.
- **Octal**: carry if sum ≥ 8 (subtract 8 from the visible digit).
- **Binary**: carry if sum ≥ 2. (1+1=10, 1+1+1=11).
- **Hex**: carry if sum ≥ 16.

### 1.10 BCD (Binary Coded Decimal)
- Each decimal digit becomes a 4-bit code (0000–1001). Codes 1010–1111 are **invalid**.
- e.g. $37_{10}$ in BCD = `0011 0111` (≠ binary `100101`).

**BCD addition (work column by column, right→left)**:
1. Add the two digits + carry (treat as hex).
2. If column sum > 9 (i.e. result is A–F **or** there was a carry out), **add 6** to correct it.
3. Otherwise add 0. Carry the result to the next column.

---

## MODULE 2 — Symbolic logic

### 2.1 Propositions & connectives
A **proposition** has a definite truth value (T=1, F=0).

| Name | Symbol | Read as |
|------|--------|---------|
| NOT | $\sim p$ (or $\neg p$, $p'$) | "not p" |
| AND | $p \land q$ | "p and q" |
| OR  | $p \lor q$ | "p or q" (inclusive) |
| IF…THEN | $p \to q$ | "if p then q" / "p implies q" |

### 2.2 Truth tables (memorise!)

| p | q | ¬p | p∧q | p∨q | p→q | p↔q |
|---|---|----|----|-----|-----|-----|
| 0 | 0 | 1  | 0  | 0   | **1** | 1 |
| 0 | 1 | 1  | 0  | 1   | **1** | 0 |
| 1 | 0 | 0  | 0  | 1   | **0** | 0 |
| 1 | 1 | 0  | 1  | 1   | 1     | 1 |

Key: $p \to q$ is **only false when** p=1, q=0.

### 2.3 Special results
- **Tautology**: true for every row (e.g. $p \lor \sim p$).
- **Contradiction**: false for every row (e.g. $p \land \sim p$).
- **Logical equivalence** ($\equiv$): same truth-table column.

### 2.4 Key equivalences
- **Double negation**: $\sim(\sim p) \equiv p$.
- **De Morgan's**:
  - $\sim(p \land q) \equiv \sim p \lor \sim q$
  - $\sim(p \lor q) \equiv \sim p \land \sim q$
- **Distributive**:
  - $p \land (q \lor r) \equiv (p \land q) \lor (p \land r)$
  - $p \lor (q \land r) \equiv (p \lor q) \land (p \lor r)$
- **Conditional rewrites**:
  - $p \to q \equiv \sim p \lor q$
  - $\sim(p \to q) \equiv p \land \sim q$

### 2.5 Conditional, contrapositive, converse
Starting from $p \to q$:
- **Contrapositive**: $\sim q \to \sim p$  *(equivalent to the original)*
- **Converse**: $q \to p$  *(NOT equivalent)*
- **Inverse**: $\sim p \to \sim q$  *(NOT equivalent)*

### 2.6 Arguments
Write as $P_1, P_2, \dots, P_n \mid C$. The argument is **valid** iff in every row where **all** premises are 1, the conclusion is also 1.
- To prove **invalid**: find at least one row where all premises are 1 but conclusion is 0.
- If no row has all premises true, the argument is **vacuously valid**.

---

## MODULE 3 — Boolean algebra & logic circuits

### 3.1 Notation (Boolean vs logic)
| Logic | Boolean |
|-------|---------|
| T / F | 1 / 0 |
| AND $\land$ | $\cdot$ (often omitted: $xy$) |
| OR $\lor$ | $+$ |
| NOT $\sim p$ | $p'$ |

**Order of operations**: complement (') ⇒ multiplication (·) ⇒ addition (+). Use brackets to override.

### 3.2 Laws of Boolean algebra

| Law | (a) | (b) |
|-----|-----|-----|
| Idempotent | $a+a=a$ | $a \cdot a = a$ |
| Complement | $a+a'=1$ | $a \cdot a'=0$ |
| Involution | $(a')'=a$ | — |
| Identity | $a+0=a$, $a+1=1$ | $a \cdot 0=0$, $a \cdot 1=a$ |
| Commutative | $a+b=b+a$ | $ab=ba$ |
| Associative | $(a+b)+c=a+(b+c)$ | $(ab)c=a(bc)$ |
| Distributive | $a(b+c)=ab+ac$ | $a+bc=(a+b)(a+c)$ |
| De Morgan | $(a+b)'=a'b'$ | $(ab)'=a'+b'$ |

Extended De Morgan: $(w+x+y+z)' = w'x'y'z'$ and $(wxyz)' = w'+x'+y'+z'$.

### 3.3 Products & sums of products (SOP)
- **Product**: variables ANDed together, e.g. $xy'z$.
- **SOP**: products ORed together, e.g. $xy + y'z + x'yz'$.
- **Fundamental product**: every variable appears (with or without '). For *n* variables there are $2^n$ fundamental products.
- **CSOP (Complete SOP)**: a SOP where every term is a fundamental product.

### 3.4 Truth table ⇄ Boolean expression
- For each row where output = 1, write its fundamental product (variable if 1, complement if 0). OR them ⇒ CSOP.
- Example row $x=0, y=1, z=0$, output 1 ⇒ term $x'yz'$.

### 3.5 Expanding a SOP to CSOP
If a term is missing variable $v$, multiply by $(v+v')$:
- $xy' = xy'(z+z') = xy'z + xy'z'$.
- $z = z(x+x')(y+y') = xyz + xy'z + x'yz + x'y'z$.

### 3.6 Logic gates

| Gate | Output |
|------|--------|
| AND  | 1 only if **all** inputs are 1 |
| OR   | 1 if **any** input is 1 |
| NOT  | output = complement of input |
| NAND | $(x \cdot y)'$ — universal gate |

**Circuit → expression**: label each gate's output as you trace forward.

**Expression → circuit**: build from innermost subexpressions outward; one NOT/AND/OR gate per operation.

### 3.7 Simplifying with De Morgan (typical trick)
Use De Morgan to "push" complements inward and remove brackets, producing a SOP:
- $(x+y'z)' = x' \cdot (y'z)' = x'(y+z') = x'y + x'z'$.

---

## MODULE 4 — Karnaugh maps & circuit design

### 4.1 Layout reminders
- Adjacent cells differ by exactly **one** variable (use Gray-code order along axes).
- **3-var K-map** (8 cells): rows = $x$, columns = $yz$ in order $00, 01, 11, 10$.
- **4-var K-map** (16 cells): rows = $wx$ in order $00,01,11,10$; columns = $yz$ in same order.
- A cell holds 1 if its fundamental product is in the SOP.

### 4.2 Grouping rules (to find a Min SOP)
1. Groups must contain a **power of 2** cells: 1, 2, 4, 8, 16.
2. Groups must be **rectangular** and contain only 1s.
3. Make groups **as large as possible** (the larger the group, the fewer variables in the product).
4. **Overlap** groups freely if it makes them larger.
5. **Wrap-around** is allowed: left-right edges and top-bottom edges are adjacent.
6. Use the **fewest groups** that still cover every 1.
7. Read off each group's product (variables that stay constant across the group; drop variables that change).

### 4.3 Min SOP procedure
- **CSOP**: every 1-cell as its own fundamental product (no simplification).
- **Min SOP**: groups chosen to minimise number of terms and number of literals.
- A Min SOP is *not unique*; multiple equally-minimal answers may exist.

### 4.4 Design problems
**Type 1: Truth table → circuit**
1. Read truth table → CSOP.
2. Place 1s in K-map.
3. Group to find Min SOP.
4. Draw the minimal AND-OR circuit.

**Type 2: Simplify a circuit**
1. Circuit → Boolean expression.
2. Expand to SOP if needed.
3. Plot in K-map → Min SOP.
4. Draw new minimal AND-OR circuit.

### 4.5 NAND gates & universality
- NAND output: $(x \cdot y)'$.
- NAND is **universal**: NOT, AND, and OR can each be built from NANDs:
  - NOT: connect both inputs to same signal → $(x \cdot x)' = x'$.
  - AND: NAND then NAND output to itself (= NOT a NAND).
  - OR: invert each input via NAND, then NAND the results: $((x')(y'))' = x+y$.

### 4.6 Converting AND-OR circuit → NAND-only
Start with a SOP. Apply double negation, then De Morgan:
$$L = xy'z + x'y = \bigl[(xy'z + x'y)'\bigr]' = \bigl[(xy'z)' \cdot (x'y)'\bigr]'$$
which is a NAND of NANDs.

---

## MODULE 5 — Predicates, quantifiers & sets

### 5.1 Predicates
A **predicate** has variables: $P(x): x>20$. Substituting values gives a proposition with a truth value.

### 5.2 Quantifiers

| Symbol | Reading | Use |
|--------|---------|-----|
| $\forall$ | "for all" / "for every" / "none" (with negation) | universal |
| $\exists$ | "there exists" / "some" / "at least one" | existential |

- $\forall x \in S, P(x)$ — every member of S satisfies P.
- $\exists x \in S, P(x)$ — at least one member satisfies P.

### 5.3 Negation of quantifiers
Swap quantifier and negate the predicate:
- $\sim(\forall x, P(x)) \equiv \exists x, \sim P(x)$
- $\sim(\exists x, P(x)) \equiv \forall x, \sim P(x)$

| Statement | Negation |
|-----------|----------|
| All do… | Some do not… |
| All are… | Some are not… |
| Some do… | None do… / All do not… |
| Some are… | None are… |

### 5.4 Two-quantifier statements
**Order matters.**
- $\forall x \exists y, S(x,y)$ — for each $x$, *some* (possibly different) $y$ works.
- $\exists y \forall x, S(x,y)$ — one *single* $y$ works for every $x$ (stronger).

**Negation rule**: flip every $\forall \leftrightarrow \exists$ and negate the predicate.
- $\sim(\forall x \exists y, S(x,y)) \equiv \exists x \forall y, \sim S(x,y)$
- $\sim(\exists y \forall x, S(x,y)) \equiv \forall y \exists x, \sim S(x,y)$

### 5.5 Sets — basics
- $\in$ = "is an element of"; $\notin$ = "is not".
- Standard sets: $\mathbb{N}$ (natural, $\{1,2,3,\dots\}$), $\mathbb{Z}$ (integers), $\mathbb{Q}$ (rationals), $\mathbb{R}$ (reals).
- Empty set: $\emptyset$ or $\{\}$. Universal set: $U$.
- Set-builder: $\{x \mid x \in \mathbb{N}, x<10\}$.
- Order/repetition don't matter: $\{a,b,c\} = \{a,a,c,b\}$.

### 5.6 Subset & set operations
- $B \subseteq A$ iff every element of B is in A.
- **Union**: $A \cup B = \{x \mid x \in A \lor x \in B\}$.
- **Intersection**: $A \cap B = \{x \mid x \in A \land x \in B\}$.
- **Complement**: $A' = \{x \in U \mid x \notin A\}$.
- **Disjoint**: $A \cap B = \emptyset$.

### 5.7 Laws of sets (mirror Boolean / logic)

| Law | Form |
|-----|------|
| Distributive | $A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$ |
|              | $A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$ |
| De Morgan | $(A \cup B)' = A' \cap B'$ |
|           | $(A \cap B)' = A' \cup B'$ |

**Correspondences**: $\cup \leftrightarrow \lor$, $\cap \leftrightarrow \land$, $' \leftrightarrow \sim$, $U \leftrightarrow T$, $\emptyset \leftrightarrow F$.

### 5.8 The Addition Principle (Inclusion–Exclusion)
For finite sets with $n(\cdot)$ = number of elements:
- **Two sets**: $n(A \cup B) = n(A) + n(B) - n(A \cap B)$.
- **Disjoint**: $n(A \cup B) = n(A) + n(B)$.
- **Three sets**:
$$n(A\cup B\cup C) = n(A)+n(B)+n(C) - n(A\cap B) - n(A\cap C) - n(B\cap C) + n(A\cap B\cap C).$$

**Venn-diagram method** (works every time): label each region with an unknown ($x$ for the centre), build equations from the given counts, solve.

### 5.9 Power set
The set of **all subsets**, including $\emptyset$ and the set itself.
- If $|S| = n$, then $|\mathcal{P}(S)| = 2^n$.
- e.g. $S = \{a,b\} \Rightarrow \mathcal{P}(S) = \{\emptyset, \{a\}, \{b\}, \{a,b\}\}$.

### 5.10 Cartesian product
$$A \times B = \{(x,y) \mid x \in A, y \in B\}$$
- Ordered pairs: $(2,5) \neq (5,2)$.
- $|A \times B| = |A| \cdot |B|$.

---

## QUICK REFERENCE — CROSS-MODULE LINKS
| Logic | Boolean | Sets |
|-------|---------|------|
| $\sim p$ | $p'$ | $A'$ |
| $p \land q$ | $pq$ | $A \cap B$ |
| $p \lor q$ | $p+q$ | $A \cup B$ |
| Tautology (T) | 1 | $U$ |
| Contradiction (F) | 0 | $\emptyset$ |
| Distributive / De Morgan apply identically in all three columns. |

---

## EXAM TIPS
1. **Always write the base subscript** in number-system answers — losing it is a silly mark.
2. For K-maps: draw the map, **circle groups in a power of 2**, and explicitly list each group's product. Don't simplify past SOP form.
3. When checking arguments, **build the full truth table** and highlight the premise-true rows.
4. To negate "All A are B" say "Some A are not B" — *not* "No A is B".
5. For BCD: if your column sum looks like a hex letter (A–F) **or** produces a carry, add 6.
6. The contrapositive is equivalent to the original; the converse is **not**.
7. $\forall \exists$ vs $\exists \forall$: order matters; the second is always stronger.
8. For 3-set Venn problems, **let $x$ = "all three"** and write every region in terms of $x$ before solving.
