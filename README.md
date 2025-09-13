# 🧮 Booth's Algorithm

Booth’s Algorithm is a binary multiplication technique used for **signed integers** in **two’s complement representation**.  
It reduces the number of additions/subtractions by efficiently handling consecutive 1’s in the multiplier.

---

## ⚙️ How It Works
1. Initialize:
   - **A** = 0 (Accumulator)
   - **Q** = Multiplier
   - **Q₋₁** = 0 (Extra bit)
   - **M** = Multiplicand
   - **Counter** = Number of bits

2. Repeat until Counter = 0:
   - If `Q0Q₋₁ = 01` → `A = A + M`
   - If `Q0Q₋₁ = 10` → `A = A - M`
   - If `Q0Q₋₁ = 00` or `11` → Do nothing
   - Perform **Arithmetic Right Shift (ARS)** on `(A, Q, Q₋₁)`
   - Decrease Counter by 1

3. Final result = Concatenation of `(A, Q)`

---

## 🔢 Example: Multiply 3 × -4 (4-bit numbers)

- Multiplicand (M) = `0011` (3)  
- Multiplier (Q) = `1100` (-4)  
- A = `0000`, Q₋₁ = `0`  

| Step | A      | Q      | Q₋₁ | Action            |
|------|--------|--------|-----|-------------------|
| Init | 0000   | 1100   | 0   | Initial values    |
| 1    | 1101   | 1100   | 0   | A = A - M (Q0Q₋₁=10) |
| →    | 1110   | 1110   | 0   | ARS               |
| 2    | 1110   | 1110   | 0   | Do nothing (Q0Q₋₁=00) |
| →    | 1111   | 0111   | 0   | ARS               |
| 3    | 0100   | 0111   | 0   | A = A + M (Q0Q₋₁=01) |
| →    | 0010   | 0011   | 1   | ARS               |
| 4    | 0010   | 0011   | 1   | Do nothing (Q0Q₋₁=11) |
| →    | 0001   | 0001   | 1   | ARS               |

**Final Result = `11110100` (-12 in decimal)** ✅

---

## 📌 Advantages
- Handles **positive and negative numbers** uniformly  
- Efficient when multiplier has consecutive 1’s  
- Reduces the number of arithmetic operations  

---

## 📖 References
- Booth, A. D. (1951). "A Signed Binary Multiplication Technique."  
- Computer Organization & Architecture textbooks  

