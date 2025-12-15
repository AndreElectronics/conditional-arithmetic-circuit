# Conditional Adder/Subtractor Circuit

## Overview
This circuit implements an arithmetic unit that performs different operations based on the relationship between two 2-bit binary numbers (A and B), where A ≥ B is always true.

## Functionality
The circuit performs the following conditional operations:

1. **When A = B**:  
   `Z = A + 1`

2. **When A > B**:  
   `Z = (A - B) - 1`

## Truth Table

| A1 | A0 | B1 | B0 | Condition | Operation       | Z2 | Z1 | Z0 | Decimal |
|----|----|----|----|-----------|-----------------|----|----|----|---------|
| 0  | 0  | 0  | 0  | A = B     | 00 + 1 = 01     | 0  | 0  | 1  | 1       |
| 0  | 1  | 0  | 0  | A > B     | (01 - 00) - 1 = 00 | 0  | 0  | 0  | 0       |
| 0  | 1  | 0  | 1  | A = B     | 01 + 1 = 10     | 0  | 1  | 0  | 2       |
| 1  | 0  | 0  | 0  | A > B     | (10 - 00) - 1 = 01 | 0  | 0  | 1  | 1       |
| 1  | 0  | 0  | 1  | A > B     | (10 - 01) - 1 = 00 | 0  | 0  | 0  | 0       |
| 1  | 0  | 1  | 0  | A = B     | 10 + 1 = 11     | 0  | 1  | 1  | 3       |
| 1  | 1  | 0  | 0  | A > B     | (11 - 00) - 1 = 10 | 0  | 1  | 0  | 2       |
| 1  | 1  | 0  | 1  | A > B     | (11 - 01) - 1 = 01 | 0  | 0  | 1  | 1       |
| 1  | 1  | 1  | 0  | A > B     | (11 - 10) - 1 = 00 | 0  | 0  | 0  | 0       |
| 1  | 1  | 1  | 1  | A = B     | 11 + 1 = 100    | 1  | 0  | 0  | 4       |

## Design Notes
- Inputs: A[1:0], B[1:0] (2 bits each)
- Output: Z[2:0] (3 bits to cover all possible results)
- Constraint: Always A ≥ B
- Technology: Standard TTL logic gates and MSI components

## Implementation Approach
1. The circuit uses magnitude comparison logic to determine if A = B or A > B
2. Based on the comparison result, appropriate control signals select the operation
3. Arithmetic operations are implemented using standard digital logic techniques
4. Two's complement method is employed for subtraction operations
