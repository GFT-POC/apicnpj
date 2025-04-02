# Documentation: `CodigoUtil.java`

## Overview
The `CodigoUtil` class provides utility methods for validating Brazilian CNPJ numbers. A CNPJ (Cadastro Nacional da Pessoa Jurídica) is a unique identifier for companies registered in Brazil. This class includes logic to verify the validity of a CNPJ based on its checksum calculation.

---

## Class: `CodigoUtil`

### Package
`com.example.supplier.util`

### Purpose
The class is designed to validate CNPJ numbers using the standard algorithm defined by Brazilian regulations. It includes a method to perform the validation and a `main` method for testing purposes.

---

## Methods

### `isValidCNPJ(long cnpj)`
#### Description
Validates a given CNPJ number by checking its checksum digits. The method uses two sets of weights to calculate the checksum and compares the calculated digits with the actual digits in the CNPJ.

#### Parameters
| Name  | Type   | Description                          |
|-------|--------|--------------------------------------|
| `cnpj` | `long` | The CNPJ number to be validated.    |

#### Return Value
| Type      | Description                              |
|-----------|------------------------------------------|
| `boolean` | Returns `true` if the CNPJ is valid, otherwise `false`. |

#### Logic
1. Converts the `long` CNPJ number into a 14-character string.
2. Validates the length of the CNPJ string (must be 14 characters).
3. Calculates the first checksum digit using the first set of weights (`weight1`).
4. Calculates the second checksum digit using the second set of weights (`weight2`).
5. Compares the calculated checksum digits with the actual digits in the CNPJ.
6. Returns `true` if both checksum digits match; otherwise, returns `false`.

#### Exception Handling
If any error occurs during the validation process (e.g., invalid characters in the CNPJ string), the method catches the exception and returns `false`.

---

### `main(String[] args)`
#### Description
A test method to demonstrate the usage of the `isValidCNPJ` method. It validates a sample CNPJ number and prints the result to the console.

#### Parameters
| Name  | Type         | Description                          |
|-------|--------------|--------------------------------------|
| `args` | `String[]`   | Command-line arguments (not used).  |

#### Example Output
```
CNPJ is valid: false
```

---

## Insights

### CNPJ Validation Algorithm
The validation algorithm uses two sets of weights to calculate checksum digits:
- **Weight Set 1**: `{5, 4, 3, 2, 9, 8, 7, 6, 5, 4, 3, 2}`
- **Weight Set 2**: `{6, 5, 4, 3, 2, 9, 8, 7, 6, 5, 4, 3, 2}`

The checksum digits are calculated as follows:
1. Multiply each digit of the CNPJ (excluding the checksum digits) by the corresponding weight.
2. Sum the results.
3. Compute the modulus (`mod`) of the sum by 11.
4. Determine the checksum digit:
   - If `mod < 2`, the checksum digit is `0`.
   - Otherwise, the checksum digit is `11 - mod`.

### Error Handling
The method gracefully handles errors, such as invalid input or unexpected exceptions, by returning `false`. This ensures robustness in real-world scenarios.

### Limitations
- The method assumes the input CNPJ is numeric and does not handle formatted CNPJ strings (e.g., `12.345.678/0001-95`).
- The validation does not check for other business rules related to CNPJ, such as reserved or invalid sequences.

### Practical Use
This utility can be integrated into systems that require validation of CNPJ numbers, such as registration forms or data processing pipelines for Brazilian companies.

---

## File Metadata
| Key         | Value               |
|-------------|---------------------|
| `FILE_NAME` | `CodigoUtil.java`   |
