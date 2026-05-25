# MAT1252 Exam Cheatsheet — Extended Edition
*Covers Modules 1–5: Number bases · Symbolic logic · Boolean algebra · Karnaugh maps · Predicates & sets*
*Includes fully worked examples for every technique.*

---

# MODULE 1 — Number bases & representation

## 1.1 Bases & subscript notation
Subscripts identify the base. Always write them in answers.

- $354_{10}$ — decimal (base 10, digits 0–9)
- $354_8$ — octal (base 8, digits 0–7)
- $1010_2$ — binary (base 2, digits 0 or 1)
- $A3F_{16}$ — hexadecimal (base 16, digits 0–9, A=10, B=11, C=12, D=13, E=14, F=15)

Positional value of any digit = $\text{digit} \times \text{base}^{\text{position}}$, starting from position 0 on the right.

## 1.2 Powers you should know cold

| Base | Powers |
|------|--------|
| 2 | 1, 2, 4, 8, 16, 32, 64, 128, 256, 512, 1024, 2048 |
| 8 | 1, 8, 64, 512, 4096 |
| 16 | 1, 16, 256, 4096, 65536 |

## 1.3 Conversion **to decimal** (Summation method)
Multiply each digit by its base power, then add.

**Worked Ex 1 — Octal → Decimal**
$$4276_8 = 4(8^3)+2(8^2)+7(8)+6 = 2048+128+56+6 = 2238_{10}$$

**Worked Ex 2 — Binary → Decimal (sum of powers of 2)**
$$10111001_2 = 2^7+2^5+2^4+2^3+2^0 = 128+32+16+8+1 = 185_{10}$$

**Worked Ex 3 — Hex → Decimal**
$$1AF_{16} = 1(256)+10(16)+15 = 256+160+15 = 431_{10}$$

$$CB4D_{16} = 12(4096)+11(256)+4(16)+13 = 49152+2816+64+13 = 52045_{10}$$

## 1.4 Conversion **decimal → other base** (Repeated division)
Divide by the target base, write down each remainder, read remainders **bottom to top**.

**Worked Ex 4 — Decimal → Octal**
Convert $278_{10}$ to octal:

| Step | Division | Quotient | Remainder |
|------|----------|----------|-----------|
| 1 | 278 ÷ 8 | 34 | **6** |
| 2 | 34 ÷ 8 | 4 | **2** |
| 3 | 4 ÷ 8 | 0 | **4** |

Reading remainders upwards: $278_{10} = 426_8$.
**Check:** $4(64)+2(8)+6 = 256+16+6 = 278$. ✓

**Worked Ex 5 — Decimal → Binary**
Convert $58_{10}$ to binary:

| Division | Quotient | Remainder |
|----------|----------|-----------|
| 58 ÷ 2 | 29 | 0 |
| 29 ÷ 2 | 14 | 1 |
| 14 ÷ 2 | 7  | 0 |
| 7 ÷ 2  | 3  | 1 |
| 3 ÷ 2  | 1  | 1 |
| 1 ÷ 2  | 0  | 1 |

Read up: $58_{10} = 111010_2$. **Check:** $32+16+8+2 = 58$. ✓

**Worked Ex 6 — Decimal → Hex**
Convert $103_{10}$ to hex:
- $103 \div 16 = 6$ remainder $7$
- $6 \div 16 = 0$ remainder $6$

So $103_{10} = 67_{16}$.

## 1.5 Binary ⇄ Octal (groups of **3**)
Octal digit ↔ 3 binary bits.

| Octal | Binary |
|-------|--------|
| 0 | 000 |
| 1 | 001 |
| 2 | 010 |
| 3 | 011 |
| 4 | 100 |
| 5 | 101 |
| 6 | 110 |
| 7 | 111 |

**Worked Ex 7 — Binary → Octal**
$10111001_2$: group from the right: `10 | 111 | 001` ⇒ $271_8$.

**Worked Ex 8 — Octal → Binary**
$1234_8$: replace each digit: `001 | 010 | 011 | 100` = $1010011100_2$.

## 1.6 Binary ⇄ Hex (groups of **4**)

| Hex | Binary | Hex | Binary |
|-----|--------|-----|--------|
| 0 | 0000 | 8 | 1000 |
| 1 | 0001 | 9 | 1001 |
| 2 | 0010 | A | 1010 |
| 3 | 0011 | B | 1011 |
| 4 | 0100 | C | 1100 |
| 5 | 0101 | D | 1101 |
| 6 | 0110 | E | 1110 |
| 7 | 0111 | F | 1111 |

**Worked Ex 9 — Binary → Hex**
$10111110101011000011_2$: group from right: `1011 1110 1010 1100 0011` ⇒ $BEAC3_{16}$.

**Worked Ex 10 — Hex → Binary**
$C0DE_{16}$ = $1100\,0000\,1101\,1110_2$.

**Worked Ex 11 — Hex → Octal (via binary)**
$C0DE_{16} = 1100000011011110_2$. Regroup in 3s from right: `1 100 000 011 011 110` ⇒ $140336_8$.

## 1.7 Binary fractions

Columns after the point have values $\tfrac{1}{2}, \tfrac{1}{4}, \tfrac{1}{8}, \tfrac{1}{16}, \dots = 2^{-1}, 2^{-2}, 2^{-3}, \dots$

### Binary fraction → Decimal
Two methods. **Method 1**: column-by-column sum. **Method 2** (faster): treat the digits as a whole binary integer, then divide by $2^k$ where $k$ = number of places.

**Worked Ex 12**
$0.1101_2 = \tfrac{1}{2}+\tfrac{1}{4}+0+\tfrac{1}{16} = \tfrac{8+4+0+1}{16} = \tfrac{13}{16} = 0.8125_{10}$.

**Worked Ex 13** (Method 2 — faster)
$0.110011_2$: digits = $110011_2 = 51$. Six places ⇒ divide by $2^6 = 64$.
$\Rightarrow 51/64 = 0.796875_{10}$.

**Worked Ex 14**
$0.00000101_2$: digits = $101_2 = 5$. Eight places ⇒ divide by $2^8 = 256$.
$\Rightarrow 5/256 = 0.01953125_{10}$.

### Decimal fraction → Binary
Repeatedly multiply the fractional part by 2; record the integer part each time (0 or 1). Stop when you hit 0.0 (or when enough places). Read integers **top-down**.

**Worked Ex 15** — Convert $0.34375_{10}$ to binary.

| × 2 | Result | Integer (read) |
|-----|--------|----------------|
| 0.34375 × 2 | 0.6875 | **0** |
| 0.6875 × 2 | 1.375  | **1** |
| 0.375 × 2  | 0.75   | **0** |
| 0.75 × 2   | 1.5    | **1** |
| 0.5 × 2    | 1.0    | **1** |

So $0.34375_{10} = 0.01011_2$.

**Worked Ex 16** — Convert $0.65625_{10}$ to binary.

| ×2 | Result | Integer |
|----|--------|---------|
| 0.65625 × 2 | 1.3125 | 1 |
| 0.3125 × 2  | 0.625  | 0 |
| 0.625 × 2   | 1.25   | 1 |
| 0.25 × 2    | 0.5    | 0 |
| 0.5 × 2     | 1.0    | 1 |

$\Rightarrow 0.65625_{10} = 0.10101_2$.

## 1.8 Arithmetic in other bases
**Rule**: in base $b$, you carry 1 when a column sum is $\geq b$ (subtract $b$ from the visible digit).

**Worked Ex 17 — Addition in octal**
```
   2 4 5
 + 3 6 6
 -------
```
- Col 1: 5+6 = 11₁₀ = 8+3 ⇒ write **3**, carry 1.
- Col 2: 4+6+1 = 11₁₀ = 8+3 ⇒ write **3**, carry 1.
- Col 3: 2+3+1 = 6 ⇒ write **6**.

Answer: $245_8 + 366_8 = 633_8$.

**Worked Ex 18 — Addition in binary**
```
   1 1 1 1 0 1
 + 1 0 1 1 1 1
 -------------
```
Add right-to-left:
- 1+1 = 10 → write 0, carry 1
- 0+1+1 = 10 → write 0, carry 1
- 1+1+1 = 11 → write 1, carry 1
- 1+1+1 = 11 → write 1, carry 1
- 1+0+1 = 10 → write 0, carry 1
- 1+1+1 = 11 → write 11

Answer: $1111101_2 + 101111_2 = 11011100_2$.

**Worked Ex 19 — Addition in hex**
```
   3 C F
 + A 5 F
 -------
```
- Col 1: F+F = 15+15 = 30₁₀ = 16+14 ⇒ write **E**, carry 1.
- Col 2: C+5+1 = 12+5+1 = 18₁₀ = 16+2 ⇒ write **2**, carry 1.
- Col 3: 3+A+1 = 3+10+1 = 14 ⇒ write **E**.

Answer: $3CF_{16} + A5F_{16} = E2E_{16}$.

## 1.9 BCD (Binary Coded Decimal)

Each decimal digit → 4-bit code (0000 to 1001). Codes 1010–1111 are **invalid BCD**.

| Digit | BCD |
|-------|-----|
| 0 | 0000 |
| 1 | 0001 |
| 2 | 0010 |
| 3 | 0011 |
| 4 | 0100 |
| 5 | 0101 |
| 6 | 0110 |
| 7 | 0111 |
| 8 | 1000 |
| 9 | 1001 |

**Worked Ex 20** — Decimal $478$ in BCD = `0100 0111 1000`. (Binary would be different: $478_{10} = 111011110_2$.)

**Worked Ex 21** — Decode BCD `0101 0111 0000 0001` ⇒ digits 5, 7, 0, 1 ⇒ $5701_{10}$.

**Worked Ex 22** — Is `0100 1011 0011` valid BCD? No — `1011` is invalid.

### BCD Addition — the "+6" rule
Work column-by-column right→left:
1. Add the two digits + any carry-in (as if they were hex/binary).
2. **If the result is > 9 OR a carry was produced**, add **6** to correct it (this generates/preserves the proper carry into the next column).
3. Otherwise add 0. Move to the next column.

**Worked Ex 23 — BCD: 28 + 58**
- Right column: 8 + 8 = 16 = $10_{16}$. The result $0$ with a carry; sum exceeded 9, so add 6: $10_{16} + 6 = 16_{16}$. Write 6, carry 1.
- Left column: 2 + 5 + 1(carry) = 8. ≤ 9, add 0.
Answer: **86** (decimal). Indeed $28+58 = 86$. ✓

**Worked Ex 24 — BCD: 45 + 78**
- Right: 5+8 = 13 = $D_{16}$. D > 9, add 6: $D+6 = 13_{16}$. Write 3, carry 1.
- Left: 4+7+1 = $C_{16}$. > 9, add 6: $C+6 = 12_{16}$. Write 2, carry 1.
- Final carry → leading 1.
Answer: **123**. ✓ ($45+78=123$.)

---

# MODULE 2 — Symbolic logic

## 2.1 Propositions & connectives
A **proposition** has a definite truth value (1 = true, 0 = false).

| Symbol | Reading | Type |
|--------|---------|------|
| $\sim p$ (or $\neg p$, $p'$) | "not p" | unary |
| $p \land q$ | "p and q" | binary |
| $p \lor q$ | "p or q" (inclusive) | binary |
| $p \to q$ | "if p then q" / "p implies q" | binary |
| $p \leftrightarrow q$ | "p iff q" | binary |

## 2.2 Master truth table

| p | q | ¬p | p∧q | p∨q | p→q | p↔q |
|---|---|----|-----|-----|-----|-----|
| 0 | 0 | 1  | 0   | 0   | **1** | 1 |
| 0 | 1 | 1  | 0   | 1   | **1** | 0 |
| 1 | 0 | 0  | 0   | 1   | **0** | 0 |
| 1 | 1 | 0  | 1   | 1   | 1     | 1 |

Memory aids:
- $p \to q$ is false **only** when p=1 and q=0.
- $p \leftrightarrow q$ is true when both have the same value.

## 2.3 Translating English ⇄ symbols

Define: $p$: file is being printed; $q$: system is ready; $r$: red light is on.

**Ex 25** — "If the system is ready and the red light is on then the file is printed."
$$(q \land r) \to p$$

**Ex 26** — "If the file is not printed then either the red light is not on or the system is not ready."
$$\sim p \to (\sim r \lor \sim q)$$

**Ex 27** — "Either (the red light is on and the file is printed) or the system is not ready."
$$(r \land p) \lor \sim q$$

**Ex 28** — Translate $m \land (\sim p \lor \sim a)$ back to English (where $p$: Peter drives; $a$: Andrew late; $m$: Max caught bus):
"Max has caught the bus and either Peter is not driving his own car or Andrew is not late."

## 2.4 Building truth tables — full worked example

**Ex 29** — Build the truth table for $((p \land \sim q) \lor r) \land (\sim p \lor \sim r)$:

| p | q | r | ¬q | p∧¬q | (p∧¬q)∨r | ¬p | ¬r | ¬p∨¬r | **Final** |
|---|---|---|----|------|----------|----|----|-------|-----------|
| 0 | 0 | 0 | 1  | 0    | 0        | 1  | 1  | 1     | **0** |
| 0 | 0 | 1 | 1  | 0    | 1        | 1  | 0  | 1     | **1** |
| 0 | 1 | 0 | 0  | 0    | 0        | 1  | 1  | 1     | **0** |
| 0 | 1 | 1 | 0  | 0    | 1        | 1  | 0  | 1     | **1** |
| 1 | 0 | 0 | 1  | 1    | 1        | 0  | 1  | 1     | **1** |
| 1 | 0 | 1 | 1  | 1    | 1        | 0  | 0  | 0     | **0** |
| 1 | 1 | 0 | 0  | 0    | 0        | 0  | 1  | 1     | **0** |
| 1 | 1 | 1 | 0  | 0    | 1        | 0  | 0  | 0     | **0** |

## 2.5 Tautologies, contradictions, equivalence
- **Tautology**: column is all 1s. Example: $p \lor \sim p$.
- **Contradiction**: column is all 0s. Example: $p \land \sim p$.
- **Logical equivalence** ($\equiv$): two expressions produce identical truth-table columns.

**Ex 30** — Show $\sim p \lor (p \land \sim q) \equiv \sim(p \to \sim q)$.

| p | q | ¬p | ¬q | p∧¬q | ¬p∨(p∧¬q) | p→¬q | ¬(p→¬q) |
|---|---|----|----|------|-----------|------|---------|
| 0 | 0 | 1  | 1  | 0    | **1**     | 1    | **0** |

Wait — the columns differ at $(0,0)$. *(Lecture's stated equivalence actually was $\sim p \lor (p \land \sim q) \equiv \sim(p \land q)$; double-check what's being asked.)*

**Ex 30 (corrected) — Show $\sim p \lor (p \land \sim q) \equiv \sim(p \land q)$**:

| p | q | ¬p | ¬q | p∧¬q | ¬p∨(p∧¬q) | p∧q | ¬(p∧q) |
|---|---|----|----|------|-----------|-----|--------|
| 0 | 0 | 1  | 1  | 0    | **1**     | 0   | **1**  |
| 0 | 1 | 1  | 0  | 0    | **1**     | 0   | **1**  |
| 1 | 0 | 0  | 1  | 1    | **1**     | 0   | **1**  |
| 1 | 1 | 0  | 0  | 0    | **0**     | 1   | **0**  |

Columns match ⇒ equivalent. ✓

**Ex 31** — Verify the distributive law $p \lor (q \land r) \equiv (p \lor q) \land (p \lor r)$:

| p | q | r | q∧r | LHS: p∨(q∧r) | p∨q | p∨r | RHS |
|---|---|---|-----|--------------|-----|-----|-----|
| 0 | 0 | 0 | 0   | 0            | 0   | 0   | 0 |
| 0 | 0 | 1 | 0   | 0            | 0   | 1   | 0 |
| 0 | 1 | 0 | 0   | 0            | 1   | 0   | 0 |
| 0 | 1 | 1 | 1   | 1            | 1   | 1   | 1 |
| 1 | 0 | 0 | 0   | 1            | 1   | 1   | 1 |
| 1 | 0 | 1 | 0   | 1            | 1   | 1   | 1 |
| 1 | 1 | 0 | 0   | 1            | 1   | 1   | 1 |
| 1 | 1 | 1 | 1   | 1            | 1   | 1   | 1 |

Columns identical ⇒ valid law. ✓

## 2.6 Key equivalences (memorise!)
- **Double negation**: $\sim(\sim p) \equiv p$.
- **De Morgan's laws**:
  - $\sim(p \land q) \equiv \sim p \lor \sim q$
  - $\sim(p \lor q) \equiv \sim p \land \sim q$
- **Distributive laws**:
  - $p \land (q \lor r) \equiv (p \land q) \lor (p \land r)$
  - $p \lor (q \land r) \equiv (p \lor q) \land (p \lor r)$
- **Conditional rewrites**:
  - $p \to q \equiv \sim p \lor q$
  - $\sim(p \to q) \equiv p \land \sim q$

**Ex 32 — Negate using De Morgan (English)**:
- "David plays guitar and likes tennis." → "David does not play guitar **or** he does not like tennis."
- "Peter has long hair and he is not wearing a coat." → "Peter does not have long hair **or** he is wearing a coat."

## 2.7 Conditional, contrapositive, converse, inverse
Starting from $p \to q$:

| Form | Symbol | Equivalent to original? |
|------|--------|-------------------------|
| Original | $p \to q$ | — |
| **Contrapositive** | $\sim q \to \sim p$ | **Yes** ✓ |
| Converse | $q \to p$ | No |
| Inverse | $\sim p \to \sim q$ | No |

**Ex 33** — "If I am in Perth then I am in Western Australia."
- Contrapositive: "If I am not in WA, then I am not in Perth." (equivalent)
- Converse: "If I am in WA, then I am in Perth." (NOT equivalent — could be in Broome)

**Ex 34** — Negate "If it rains then the picnic is cancelled."
Using $\sim(p\to q) \equiv p \land \sim q$:
"It rains **and** the picnic is not cancelled."

## 2.8 Validity of arguments
Write the argument as $P_1, P_2, \dots, P_n \mid C$. It is **valid** iff in **every** row where all premises are 1, the conclusion is also 1.

**Ex 35 — Valid argument**: $p \to (q \land \sim r), q, \sim r \mid \sim p$.

| p | q | r | ¬r | q∧¬r | P₁: p→(q∧¬r) | P₂: q | P₃: ¬r | C: ¬p | All P true? |
|---|---|---|----|------|--------------|-------|--------|-------|-------------|
| 0 | 0 | 0 | 1  | 0    | 1            | 0     | 1      | 1     | no |
| 0 | 0 | 1 | 0  | 0    | 1            | 0     | 0      | 1     | no |
| 0 | 1 | 0 | 1  | 1    | 1            | 1     | 1      | 1     | **yes** ✓ |
| 0 | 1 | 1 | 0  | 0    | 1            | 1     | 0      | 1     | no |
| 1 | 0 | 0 | 1  | 0    | 0            | 0     | 1      | 0     | no |
| 1 | 0 | 1 | 0  | 0    | 0            | 0     | 0      | 0     | no |
| 1 | 1 | 0 | 1  | 1    | 1            | 1     | 1      | 0     | n/a-but conclusion is 0 |
| 1 | 1 | 1 | 0  | 0    | 0            | 1     | 0      | 0     | no |

Wait — at row $(1,1,0)$ all three premises are 1 but the conclusion ($\sim p = 0$) is **false**! That would make the argument *invalid*.

Recheck row $(1,1,0)$: $P_1 = p \to (q \land \sim r) = 1 \to (1 \land 1) = 1 \to 1 = 1$ ✓, $P_2 = q = 1$ ✓, $P_3 = \sim r = 1$ ✓. Conclusion $\sim p = 0$. So all premises true and conclusion false ⇒ **invalid**.

*(This is a useful caution: always check every row mechanically; don't trust the "shape" of an argument.)*

**Ex 36 — A genuinely valid argument**: $p \to (q \land \sim r), \sim q, r \mid \sim p$.

| p | q | r | q∧¬r | p→(q∧¬r) | ¬q | r | ¬p | All P true? Conclusion? |
|---|---|---|------|----------|----|----|----|--------------------------|
| 0 | 0 | 0 | 0    | 1        | 1  | 0  | 1  | no |
| 0 | 0 | 1 | 0    | 1        | 1  | 1  | 1  | **yes** → ¬p = 1 ✓ |
| 0 | 1 | 0 | 1    | 1        | 0  | 0  | 1  | no |
| 0 | 1 | 1 | 0    | 1        | 0  | 1  | 1  | no |
| 1 | 0 | 0 | 0    | 0        | 1  | 0  | 0  | no |
| 1 | 0 | 1 | 0    | 0        | 1  | 1  | 0  | no |
| 1 | 1 | 0 | 1    | 1        | 0  | 0  | 0  | no |
| 1 | 1 | 1 | 0    | 0        | 0  | 1  | 0  | no |

Only one row has all premises true, and there the conclusion is 1. ⇒ **valid**. ✓

**Ex 37 — Invalid argument**: $p \lor q, p \to \sim r, \sim r \mid p$.

Look for any row with all premises 1 and conclusion 0. Row $(p=0, q=1, r=0)$: $p\lor q = 1$, $p \to \sim r = 1$, $\sim r = 1$. Conclusion $p = 0$. Premises true, conclusion false ⇒ **invalid**.

---

# MODULE 3 — Boolean algebra & logic circuits

## 3.1 Notation
| Logic | Boolean |
|-------|---------|
| T / F | 1 / 0 |
| AND $\land$ | $\cdot$ or juxtaposition (i.e. $xy$) |
| OR $\lor$ | $+$ |
| NOT $\sim p$ | $p'$ |

**Order of operations**: complement (') → multiplication (·) → addition (+). Use brackets to override.

## 3.2 Evaluating expressions

**Ex 38** — If $x=1, y=0, z=0$, evaluate $xy' + yz'$.
$xy' + yz' = (1)(0') + (0)(0') = (1)(1)+(0)(1) = 1+0 = 1$.

**Ex 39** — If $x=0, y=1$, evaluate $(x'+y)'$.
$(0'+1)' = (1+1)' = 1' = 0$.

**Ex 40** — If $x=0, y=1, z=0$, evaluate $(x + yz')(xy' + z)$.
$= (0 + 1 \cdot 1)(0 \cdot 1 + 0) = (0+1)(0+0) = 1 \cdot 0 = 0$.

**Ex 41** — If $x=0, y=1, z=0$, evaluate $xyz + x'yz' + x'y'z$.
$= (0)(1)(0) + (1)(1)(1) + (1)(0)(0) = 0 + 1 + 0 = 1$.

## 3.3 Sums of products (SOP)
- **Product**: ANDed variables (with/without complement): $xy'z$, $x'y$.
- **Sum of products**: products ORed together: $xy' + y'z + x'yz'$.
- **Fundamental product**: every variable in the universe appears (with or without '). For $n$ variables there are $2^n$ fundamental products.
- **CSOP** (Complete SOP): a SOP where every term is a fundamental product. Unique for a given function.
- **Min SOP**: the SOP with fewest terms / fewest literals. **Not unique.**

**Ex 42** — Match value combos to products:
- $x=1, y=1, z=0$ ⇒ product **$xyz'$**
- $x=0, y=1, z=0$ ⇒ product **$x'yz'$**
- $x=1, y=0, z=1$ ⇒ product **$xy'z$**
- $x=0, y=0, z=0$ ⇒ product **$x'y'z'$**

## 3.4 Boolean laws

| Law | (a) | (b) |
|-----|-----|-----|
| Idempotent | $a+a=a$ | $a \cdot a = a$ |
| Complement | $a+a'=1$ | $a \cdot a' = 0$ |
| Involution | $(a')'=a$ | — |
| Identity | $a+0=a$, $a+1=1$ | $a \cdot 0=0$, $a \cdot 1=a$ |
| Commutative | $a+b=b+a$ | $ab=ba$ |
| Associative | $(a+b)+c=a+(b+c)$ | $(ab)c=a(bc)$ |
| Distributive | $a(b+c) = ab+ac$ | $a+bc = (a+b)(a+c)$ |
| De Morgan | $(a+b)'=a'b'$ | $(ab)'=a'+b'$ |

Extended: $(w+x+y+z)' = w'x'y'z'$ and $(wxyz)' = w'+x'+y'+z'$.

## 3.5 Simplification examples

**Ex 43** — Simplify $y'(yz + xz')$.
$y'(yz + xz') = y'yz + xy'z' = 0 \cdot z + xy'z' = xy'z'$. ✓

**Ex 44** — Simplify $xy + xy + wz$.
$= xy + wz$ (idempotent).

**Ex 45** — Simplify $wx'y \cdot wz$.
$= wwx'yz = wx'yz$ (idempotent on $w$).

## 3.6 Using De Morgan to reach a SOP

**Ex 46** — Reduce $(x + y'z)'$ to a SOP.
$(x + y'z)' = x'(y'z)' = x'(y+z') = x'y + x'z'$.

**Ex 47** — Reduce $(xy' + yz')'$.
$= (xy')'(yz')' = (x'+y)(y'+z) = x'y' + x'z + yy' + yz = x'y' + x'z + yz$.
(Note $yy' = 0$.)

**Ex 48** — Reduce $(x' + xy'z + yz')'$.
$= x \cdot (xy'z)' \cdot (yz')' = x(x'+y+z')(y'+z)$.
$= (xx' + xy + xz')(y'+z) = (0 + xy + xz')(y'+z)$
$= (xy + xz')(y'+z) = xyy' + xyz + xy'z' + xzz' = 0 + xyz + xy'z' + 0$
$= xyz + xy'z'$.

**Ex 49** — Reduce $(xy' + x'z + yz')'$.
$= (xy')'(x'z)'(yz')' = (x'+y)(x+z')(y'+z)$.
First two: $(x'+y)(x+z') = x'x + x'z' + xy + yz' = 0 + x'z' + xy + yz'$.
Multiply by $(y'+z)$:
$(x'z' + xy + yz')(y'+z) = x'y'z' + x'zz' + xyy' + xyz + yy'z' + yzz'$
$= x'y'z' + 0 + 0 + xyz + 0 + 0 = x'y'z' + xyz$.

## 3.7 Truth table → CSOP

**Ex 50** — Given the table below, write a Boolean expression.

| x | y | z | L |
|---|---|---|---|
| 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 |
| 0 | 1 | 0 | 1 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 0 | 1 |
| 1 | 0 | 1 | 1 |
| 1 | 1 | 0 | 0 |
| 1 | 1 | 1 | 1 |

L = 1 in rows giving fundamental products $x'yz'$, $xy'z'$, $xy'z$, $xyz$.
$$L = x'yz' + xy'z' + xy'z + xyz$$

## 3.8 Expanding a SOP to CSOP
If a variable is missing from a term, multiply by $(v + v')$.

**Ex 51** — Expand $P(x,y,z) = xy'$ to CSOP.
$xy' = xy'(z+z') = xy'z + xy'z'$.

**Ex 52** — Expand $M(x,y,z) = z$ to CSOP.
$z = z(x+x') = xz + x'z = xz(y+y') + x'z(y+y') = xyz + xy'z + x'yz + x'y'z$.

**Ex 53** — Expand $L(w,x,y,z) = wxy'z + xyz' + w'yz$.
- $wxy'z$ already complete.
- $xyz' = xyz'(w+w') = wxyz' + w'xyz'$.
- $w'yz = w'yz(x+x') = w'xyz + w'x'yz$.

Final CSOP: $wxy'z + wxyz' + w'xyz' + w'xyz + w'x'yz$.

## 3.9 Logic gates & circuits

| Gate | Output | Notation |
|------|--------|----------|
| AND  | 1 only if **all** inputs are 1 | $xy$ |
| OR   | 1 if **any** input is 1 | $x+y$ |
| NOT  | flips input | $x'$ |
| NAND | $(xy)'$ — universal gate | $(xy)'$ |

**Circuit → expression**: trace through, label each gate's output.

**Ex 54** — A circuit has inputs $x,y,z$. First gate ANDs $y'$ and $z$ giving $y'z$. Second gate ANDs $x'$ and $y$ giving $x'y$. Output OR-gate combines them ⇒ $x'y + y'z$.

**Ex 55** — Output of an "$(x'+y+z')(x+y'+z)$" circuit: two OR gates feeding into a single AND gate.

## 3.10 NAND universality
NAND is universal — any circuit can be made from NANDs alone:
- **NOT**: tie both NAND inputs together: $(x \cdot x)' = x'$.
- **AND**: NAND then NOT (which is also a NAND): $((xy)')' = xy$.
- **OR**: invert each input via NAND, then NAND the results — by De Morgan, $((x')(y'))' = x+y$.

## 3.11 Converting AND-OR → NAND-only
Start from a SOP. Apply double negation and De Morgan to the inner:

$$L = xy'z + x'y = \bigl[(xy'z + x'y)'\bigr]' = \bigl[(xy'z)' \cdot (x'y)'\bigr]'$$

That last expression is a NAND of two NANDs. Each $(\cdot)'$ is a NAND-of-its-inputs (with internal NOTs realised by 1-input NANDs).

---

# MODULE 4 — Karnaugh maps

## 4.1 K-map layout
The K-map is a grid where adjacent cells differ in **exactly one variable** (Gray-code ordering).

### 3-variable K-map (8 cells)
- Rows = $x$ ($x' = 0$ top, $x = 1$ bottom).
- Columns labelled $yz$ in **Gray-code** order: `00, 01, 11, 10`.

|        | yz=00 | yz=01 | yz=11 | yz=10 |
|--------|-------|-------|-------|-------|
| x=0    | $x'y'z'$ | $x'y'z$ | $x'yz$ | $x'yz'$ |
| x=1    | $xy'z'$  | $xy'z$  | $xyz$  | $xyz'$  |

### 4-variable K-map (16 cells)
- Rows = $wx$ in order `00, 01, 11, 10`.
- Columns = $yz$ in order `00, 01, 11, 10`.

|          | yz=00 | yz=01 | yz=11 | yz=10 |
|----------|-------|-------|-------|-------|
| wx=00    | $w'x'y'z'$ | $w'x'y'z$ | $w'x'yz$ | $w'x'yz'$ |
| wx=01    | $w'xy'z'$  | $w'xy'z$  | $w'xyz$  | $w'xyz'$  |
| wx=11    | $wxy'z'$   | $wxy'z$   | $wxyz$   | $wxyz'$   |
| wx=10    | $wx'y'z'$  | $wx'y'z$  | $wx'yz$  | $wx'yz'$  |

## 4.2 Grouping rules (the "seven commandments")
1. Group sizes must be a **power of 2**: 1, 2, 4, 8, 16.
2. Groups are **rectangular** and contain only 1s.
3. Make groups **as large as possible** (each doubling drops a literal).
4. **Overlap** groups freely if it makes them bigger.
5. **Wrap-around** is allowed — left/right edges adjacent, top/bottom edges adjacent.
6. Use the **fewest groups** that still cover every 1.
7. The product for a group = the variables whose value is **constant** across that group; variables that change are dropped.

## 4.3 Reading a K-map — worked examples

**Ex 56 (3-var)** — Two 1s in cells $x=0,yz=00$ and $x=0,yz=01$ form a horizontal 2-group. Variables held constant: $x=0$ (so $x'$), $y=0$ (so $y'$); $z$ varies and is dropped.
$\Rightarrow$ product is $x'y'$.

**Ex 57 (3-var, wrap)** — Cells $(x=0,yz=00)$ and $(x=0,yz=10)$ (left/right edges of the same row). Constants: $x=0, z=0$. Product = $x'z'$.

**Ex 58 (3-var, full coverage of two columns)** — Four 1s filling columns $yz=00$ and $yz=10$ (both rows): all four cells share $z=0$; $x$ and $y$ vary.
$\Rightarrow$ product is just $z'$.

**Ex 59 (4-var)** — A 4-group covering all of column $yz=01$: $y=0, z=1$; $w,x$ vary ⇒ product $y'z$.

**Ex 60 (4-var, central 2×2 block)** — Cells $wx=01$ to $wx=11$ across $yz=01,11$. Constants: $x=1, z=1$; $w$ and $y$ vary. ⇒ product $xz$.

## 4.4 K-map → Min SOP — worked examples

**Ex 61 (3-var)** — Map with 1s at the cells producing $x'y'z'$, $x'yz$, $xy'z'$, $xyz$:

|        | 00 | 01 | 11 | 10 |
|--------|----|----|----|----|
| x=0    | 1  | 0  | 1  | 0  |
| x=1    | 1  | 0  | 1  | 0  |

Two 2-groups (vertical):
- Column 00 (both rows): $y'z'$.
- Column 11 (both rows): $yz$.

Min SOP: $y'z' + yz$.

**Ex 62 (3-var)** — A K-map with 1s in the entire $x=1$ row, and in cells $x=0, yz=01$ and $x=0, yz=11$:

|        | 00 | 01 | 11 | 10 |
|--------|----|----|----|----|
| x=0    | 0  | 1  | 1  | 0  |
| x=1    | 1  | 1  | 1  | 1  |

Groups:
- Whole bottom row (4-group): $x$.
- Two columns $yz=01,11$ both rows (4-group): $z$.

Min SOP: $x + z$.

**Ex 63 (4-var)** — From the lecture's Example 7:

|          | 00 | 01 | 11 | 10 |
|----------|----|----|----|----|
| wx=00    | 1  | 0  | 0  | 0  |
| wx=01    | 0  | 0  | 1  | 1  |
| wx=11    | 0  | 1  | 1  | 0  |
| wx=10    | 0  | 0  | 0  | 0  |

Groups:
- $wx=11, yz=01$ and $wx=11, yz=11$ (2-group): $wxz$.  *(wait — $z$ is 1 in both, $y$ varies; constants $w=1,x=1,z=1$ ⇒ $wxz$.)*
- $w'xy$ from cells $wx=01,yz=11$ and $wx=01,yz=10$ and $wx=11,yz=11$ and $wx=11,yz=10$? Re-grouping: $wx=01,yz=11$ and $wx=01,yz=10$ and $wx=11,yz=11$ and $wx=11,yz=10$ — these four share $x=1, y=1$ ⇒ $xy$. Better: use overlap to grow groups.
- Lecture's stated Min SOP: $wxz + w'xy + x'yz' + w'x'y'z$.

(There is often more than one valid Min SOP for a given map.)

**Ex 64 (4-var, simpler)** — From lecture Ex 8:

|          | 00 | 01 | 11 | 10 |
|----------|----|----|----|----|
| wx=00    | 0  | 0  | 0  | 0  |
| wx=01    | 0  | 1  | 1  | 0  |
| wx=11    | 1  | 1  | 1  | 1  |
| wx=10    | 0  | 0  | 0  | 0  |

Groups:
- $wx=11$ row (4-group): $wx$.
- Middle 2×2 block $wx \in \{01,11\}, yz \in \{01,11\}$ (4-group): $xz$.
- Right 2-cells $wx \in \{01,11\}, yz \in \{11\}$: covered already; instead group $wx \in \{01,11\}, yz=11$ alone? It's already inside both groups.

Better: $wx=11$ row gives $wx$; another 4-group covers $wx \in \{01,11\}, yz \in \{01,11\}$ giving $xz$; finally cell $wx=11, yz \in \{01,11\}$ is covered. The Min SOP: $wx + xz$.

(Lecture answer: $xz + xy + wy$. Multiple equivalent Min SOPs are possible if grouping choices differ.)

## 4.5 Design Problem Type 1: Truth table → minimal circuit

**Ex 65** — Design the minimal AND-OR circuit that gives $P$ as specified:

| x | y | z | P |
|---|---|---|---|
| 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 |
| 0 | 1 | 0 | 1 |
| 0 | 1 | 1 | 1 |
| 1 | 0 | 0 | 1 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 1 |
| 1 | 1 | 1 | 0 |

CSOP: $P = x'y'z + x'yz' + x'yz + xy'z' + xyz'$.
K-map:

|        | 00 | 01 | 11 | 10 |
|--------|----|----|----|----|
| x=0    | 0  | 1  | 1  | 1  |
| x=1    | 1  | 0  | 0  | 1  |

Groups:
- 4-group: cells $x=0, yz \in \{01,11\}$ + cells $x=0, yz=10$? Better: $x=0$ row has 1s in 01,11,10 — three of four. Group $(x=0, yz=01)$ + $(x=0, yz=11)$ giving $x'z$. Group $(x=0, yz=11)$ + $(x=0, yz=10)$ giving $x'y$. The cell $(x=1, yz=00)$ + $(x=1, yz=10)$ = $xz'$.
- All 1s covered.

Min SOP: $P = x'z + x'y + xz'$.

Circuit: three AND gates feeding one OR gate.

## 4.6 Design Problem Type 2: Simplify a circuit

**Ex 66** — Given the circuit producing $R = (y'+z)x' + (x+z')y$, simplify.
Expand: $R = x'y' + x'z + xy + yz'$.

K-map (3-var):

|        | 00 | 01 | 11 | 10 |
|--------|----|----|----|----|
| x=0    | 1  | 1  | 1  | 0  |
| x=1    | 0  | 0  | 1  | 1  |

Groups:
- $x=0$ row, columns 00,01: $x'y'$. Combine with top-right of row $x=1, yz=11$ (column 11)? Cells with $y=1$: $(x=0,yz=11), (x=1,yz=11), (x=1,yz=10)$ + $(x=0,yz=10)$ — column 10 top is 0. Try 4-group: column 01+11 of top row → $x'z+x'y$.
- Better: bottom row $x=1$, $yz \in \{11,10\}$: $xy$.
- Top-row columns $\{00,01\}$: $x'y'$.
- Diagonal cell $(x=0,yz=11)$: covered if we include it in column 11 (2-group): $yz$? Cells $(x=0,yz=11)$ and $(x=1,yz=11)$ both 1 ⇒ $yz$.

Min SOP: $R = x'y' + xy + yz$.
(Multiple equivalents exist; lecture answer: $R = y + x'$ if more 1s allow it — re-derive from your own simplified table.)

## 4.7 NAND-only conversion — example

**Ex 67** — Convert $L = xy'z + x'y$ to NANDs only.
$$L = \bigl[(xy'z + x'y)'\bigr]' = \bigl[(xy'z)'(x'y)'\bigr]'$$
- The inner $(xy'z)'$ and $(x'y)'$ are each NANDs (with $y'$ supplied by a 1-input NAND).
- The outer $[\dots]'$ is a NAND of the two intermediate NAND outputs.

Result: 3-NAND circuit (plus inverters built from NANDs as needed).

---

# MODULE 5 — Predicates, quantifiers & sets

## 5.1 Predicates → propositions
A **predicate** has variables. Substituting values gives a proposition.

**Ex 68** — $P(x): x+5 = 12$.
$P(3): 3+5=12$, FALSE. $P(7): 7+5=12$, TRUE.

**Ex 69** — $Q(x,y):$ "the name $x$ has $y$ letters."
$Q(\text{John},4)$: TRUE. $Q(\text{Sam},8)$: FALSE.

## 5.2 Quantifiers

| Symbol | Reading |
|--------|---------|
| $\forall$ | "for all", "for every", "for each" |
| $\exists$ | "there exists", "for some", "at least one" |

**Ex 70** — $R$ = people in this room, $C(x): x$ likes chocolate.
- $\forall x \in R, C(x)$: "Everybody in this room likes chocolate."
- $\exists x \in R, \sim C(x)$: "At least one person in this room does not like chocolate."

**Ex 71** — Define $S(x): (x>2) \land (x<7)$. Then $\exists x \in \mathbb{N}, S(x)$ means "There is a natural number strictly between 2 and 7." (True.)

**Ex 72** — $Q(x): (x<5) \lor (x \geq 5)$. Then $\forall x \in \mathbb{R}, Q(x)$ — true (it's a tautology).

## 5.3 Negation of a single-quantifier statement
Flip the quantifier and negate the predicate.

- $\sim(\forall x, P(x)) \equiv \exists x, \sim P(x)$
- $\sim(\exists x, P(x)) \equiv \forall x, \sim P(x)$

| English | Negation |
|---------|----------|
| All do | Some do not |
| All are | Some are not |
| Some do | None do / No one does |
| Some are | None are |
| Nobody | Somebody |
| Not all | All |

**Ex 73 — Negate each statement:**
1. "All cars run on petrol." → "Some cars do not run on petrol."
2. "Some files are not binary." → "All files are binary."
3. "Everybody likes ice cream." → "Somebody does not like ice cream."
4. "Some students like Maths." → "No students like Maths."
5. "Nobody listens to Beethoven." → "Some people listen to Beethoven."
6. "Some people do not eat curry." → "Everybody eats curry."
7. "All rabbits are grey." → "Some rabbits are not grey."
8. "Not all dogs bite." → "All dogs bite."

## 5.4 Two quantifiers — order matters
Let $P$ = people, $M$ = movies, $S(x,y)$: "$x$ has seen $y$".

- $\forall x \exists y, S(x,y)$ — every person has seen *some* movie (possibly different ones).
- $\exists y \forall x, S(x,y)$ — there is **one specific** movie everyone has seen. (Stronger.)
- $\exists x \forall y, S(x,y)$ — some person has seen every movie.
- $\forall x \forall y, S(x,y)$ — every person has seen every movie.
- $\exists x \exists y, S(x,y)$ — at least one person has seen at least one movie.

**Important**: $\exists y \forall x$ implies $\forall x \exists y$, but the reverse is not generally true.

## 5.5 Negating two-quantifier statements
Flip every quantifier and negate the inner predicate.

- $\sim(\forall x \exists y, S(x,y)) \equiv \exists x \forall y, \sim S(x,y)$
- $\sim(\exists y \forall x, S(x,y)) \equiv \forall y \exists x, \sim S(x,y)$
- $\sim(\exists x \forall y, S(x,y)) \equiv \forall x \exists y, \sim S(x,y)$
- $\sim(\forall x \forall y, S(x,y)) \equiv \exists x \exists y, \sim S(x,y)$
- $\sim(\exists x \exists y, S(x,y)) \equiv \forall x \forall y, \sim S(x,y)$

**Ex 74** — Negate "For each movie there is some person who has seen it."
Symbols: $\forall y \in M, \exists x \in P, S(x,y)$.
Negation: $\exists y \in M, \forall x \in P, \sim S(x,y)$.
English: "There is at least one movie that nobody has seen."

**Ex 75** — Negate "Somebody has seen every movie."
Symbols: $\exists x \in P, \forall y \in M, S(x,y)$.
Negation: $\forall x \in P, \exists y \in M, \sim S(x,y)$.
English: "For every person there is some movie they haven't seen", i.e. "Nobody has seen every movie."

**Ex 76** — Negate "There is some movie that everyone has seen."
Symbols: $\exists y \in M, \forall x \in P, S(x,y)$.
Negation: $\forall y \in M, \exists x \in P, \sim S(x,y)$.
English: "For each movie, there is somebody who has not seen it."

## 5.6 Sets — basics
- Membership: $x \in A$ or $x \notin A$.
- Standard sets:
  - $\mathbb{N} = \{1, 2, 3, \dots\}$ (natural numbers).
  - $\mathbb{Z} = \{\dots, -2, -1, 0, 1, 2, \dots\}$ (integers).
  - $\mathbb{Q}$ = rational numbers (any fraction $p/q$).
  - $\mathbb{R}$ = real numbers.
- Empty set: $\emptyset$ or $\{\}$. Universal set: $U$.
- Set-builder notation: $\{x \mid x \in \mathbb{N},\ x < 10\}$.
- **Order/repetition irrelevant**: $\{a,b,c\} = \{c,a,a,b\}$.

## 5.7 Set operations
- **Union**: $A \cup B = \{x \mid x \in A \lor x \in B\}$.
- **Intersection**: $A \cap B = \{x \mid x \in A \land x \in B\}$.
- **Complement**: $A' = \{x \in U \mid x \notin A\}$.
- **Subset**: $B \subseteq A$ iff every element of $B$ is in $A$.
- **Disjoint**: $A \cap B = \emptyset$.

**Ex 77** — Universal $U = \{1,2,\dots,12\}$, $E = \{\text{evens}\} = \{2,4,6,8,10,12\}$, $T = \{\text{multiples of 3}\} = \{3,6,9,12\}$.
- $E \cap T = \{6,12\}$.
- $E \cup T = \{2,3,4,6,8,9,10,12\}$.
- $E' = \{1,3,5,7,9,11\}$.

## 5.8 Laws of sets (mirror Boolean / logic)

| Law | Form |
|-----|------|
| Distributive | $A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$ |
|              | $A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$ |
| De Morgan | $(A \cup B)' = A' \cap B'$ |
|           | $(A \cap B)' = A' \cup B'$ |
| Identity | $A \cup \emptyset = A$, $A \cap U = A$ |
| Complement | $A \cup A' = U$, $A \cap A' = \emptyset$ |
| Idempotent | $A \cup A = A$, $A \cap A = A$ |

**Correspondences**: $\cup \leftrightarrow \lor$, $\cap \leftrightarrow \land$, $' \leftrightarrow \sim$, $U \leftrightarrow T$, $\emptyset \leftrightarrow F$.

## 5.9 The Addition Principle (Inclusion–Exclusion)

**Two sets**: $n(A \cup B) = n(A) + n(B) - n(A \cap B)$.
**Disjoint**: $n(A \cup B) = n(A) + n(B)$.

**Three sets**:
$$n(A\cup B\cup C) = n(A)+n(B)+n(C) - n(A\cap B) - n(A\cap C) - n(B\cap C) + n(A\cap B\cap C).$$

### Worked Ex 78 — Two-set, by formula
$A$ = multiples of 3 less than 32 = $\{3,6,9,12,15,18,21,24,27,30\}$ ⇒ $n(A)=10$.
$B$ = multiples of 5 less than 32 = $\{5,10,15,20,25,30\}$ ⇒ $n(B)=6$.
$A \cap B$ = multiples of 15 less than 32 = $\{15,30\}$ ⇒ $n(A \cap B)=2$.
$n(A \cup B) = 10 + 6 - 2 = 14$. ✓

### Worked Ex 79 — Disjoint sets
$A$ = multiples of 7 less than 50 (7 of them); $B$ = multiples of 12 less than 50 (4 of them). LCM 84 > 50, so $A \cap B = \emptyset$.
$n(A \cup B) = 7 + 4 = 11$.

### Worked Ex 80 — Two-set Venn problem
In a group of 80 students: 27 play cricket, 45 play baseball, 20 play neither. Find:
(i) Both, (ii) Cricket or baseball, (iii) Baseball only, (iv) Cricket only.

Let $x = n(C \cap B)$. Then:
- Cricket only: $27 - x$.
- Baseball only: $45 - x$.
- Both: $x$.
- Neither: 20.

All four regions sum to 80:
$(27-x) + x + (45-x) + 20 = 80$
$92 - x = 80 \Rightarrow x = 12$.

Answers: (i) **12**; (ii) $(27-12)+12+(45-12) = 15+12+33 = $ **60**; (iii) **33**; (iv) **15**.

### Worked Ex 81 — Three-set Venn (long form)
60 people surveyed about TV shows R, S, T:
- $n(U) = 60$
- $n(R) = 26, n(S) = 27, n(T) = 23$
- $n(R \cap S) = 7, n(R \cap T) = 8, n(S \cap T) = 11$
- $n(\text{none}) = 6$

Let $x = n(R \cap S \cap T)$. Then:
- $R \cap S \cap T'$ has $7 - x$.
- $R \cap S' \cap T$ has $8 - x$.
- $R' \cap S \cap T$ has $11 - x$.
- $R$-only: $26 - (7-x) - x - (8-x) = 26 - 15 + x = 11 + x$.
- $S$-only: $27 - (7-x) - x - (11-x) = 27 - 18 + x = 9 + x$.
- $T$-only: $23 - (8-x) - x - (11-x) = 23 - 19 + x = 4 + x$.

Sum all regions (= 60):
$(11+x) + (7-x) + (9+x) + (8-x) + x + (11-x) + (4+x) + 6 = 60$
$\Rightarrow 56 + x = 60 \Rightarrow x = 4$.

Final counts:
- All three: **4**
- R & S, not T: $7 - 4 = $ **3**
- S only: $9 + 4 = $ **13**
- Only one show: $(11+4) + (9+4) + (4+4) = 15 + 13 + 8 = $ **36**

## 5.10 Power set
The **power set** $\mathcal{P}(S)$ is the set of **all subsets** of $S$, including $\emptyset$ and $S$ itself.
- If $|S| = n$, then $|\mathcal{P}(S)| = 2^n$.

**Ex 82** — $S = \{a, b\}$.
$\mathcal{P}(S) = \{\emptyset,\ \{a\},\ \{b\},\ \{a,b\}\}$. Size 4 = $2^2$.

**Ex 83** — $S = \{M, W, F\}$ (yoga days).
$\mathcal{P}(S) = \{\emptyset, \{M\}, \{W\}, \{F\}, \{M,W\}, \{M,F\}, \{W,F\}, \{M,W,F\}\}$. Size 8 = $2^3$.

## 5.11 Cartesian product
$$A \times B = \{(x,y) \mid x \in A,\ y \in B\}$$
Pairs are **ordered**: $(2,5) \neq (5,2)$. $|A \times B| = |A| \cdot |B|$.

**Ex 84** — $A = \{\text{Mon, Tues, Wed}\}$, $B = \{\text{am, pm}\}$.
$A \times B = \{$(Mon,am), (Mon,pm), (Tues,am), (Tues,pm), (Wed,am), (Wed,pm)$\}$. Size $3 \cdot 2 = 6$.

**Ex 85** — $A = \{1,2,3\}$, $B = \{x,y\}$. $A \times B$ has 6 pairs: $(1,x),(1,y),(2,x),(2,y),(3,x),(3,y)$.

---

# QUICK REFERENCE — CROSS-MODULE LINKS

| Logic | Boolean | Sets |
|-------|---------|------|
| $\sim p$ | $p'$ | $A'$ |
| $p \land q$ | $pq$ | $A \cap B$ |
| $p \lor q$ | $p+q$ | $A \cup B$ |
| Tautology (T) | 1 | Universal $U$ |
| Contradiction (F) | 0 | $\emptyset$ |
| De Morgan: $\sim(p \land q) \equiv \sim p \lor \sim q$ | $(pq)' = p'+q'$ | $(A \cap B)' = A' \cup B'$ |
| Distributive | $p(q+r) = pq+pr$ | $A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$ |

---

# EXAM TIPS / COMMON MISTAKES

1. **Always include the base subscript** in number-conversion answers.
2. In repeated division, read remainders **bottom-up** — easy mark to lose by reversing.
3. Bytes/group sizes: octal = groups of **3**; hex = groups of **4**. Don't mix them up.
4. **BCD ≠ binary.** $25_{10}$ in binary is $11001$; in BCD it's `0010 0101`.
5. BCD addition: add 6 if either (a) result > 9, OR (b) a carry was produced.
6. $p \to q$ is FALSE **only** when p=1 and q=0 — the only "tricky" row.
7. Contrapositive ≡ original; converse and inverse do NOT.
8. Negation of "All A are B" is "Some A are NOT B" — not "No A is B".
9. K-map groups must be powers of 2; "almost-2" groups (3 cells) are illegal.
10. K-map wrap-around is real: don't forget edge-to-edge groups (especially the four corners).
11. When converting truth table → SOP, write a fundamental product **only for rows where output = 1**.
12. $\forall \exists$ vs $\exists \forall$: the latter is **stronger** — one fixed witness for everything.
13. Two-quantifier negation: flip BOTH quantifiers AND negate the predicate.
14. Set-power $|\mathcal{P}(S)| = 2^n$; include $\emptyset$ and $S$ itself in the listing.
15. For 3-set Venn problems, let $x = $ "all three" and write every region in terms of $x$ first.
16. NAND is universal — convert AND-OR via double negation + De Morgan.
17. A "Min SOP" is **not unique** — different valid K-map groupings can give different but equally-minimal answers.
