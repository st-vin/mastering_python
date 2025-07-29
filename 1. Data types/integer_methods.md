## Integer (`int`) Methods & Operations

| Method/Operation | Description                        | Usage Example                                |
| ---------------- | ---------------------------------- | -------------------------------------------- |
| `+`              | Addition                           | `5 + 3` → `8`                                |
| `-`              | Subtraction                        | `10 - 4` → `6`                               |
| `*`              | Multiplication                     | `7 * 6` → `42`                               |
| `/`              | Division (returns float)           | `15 / 4` → `3.75`                            |
| `//`             | Floor division                     | `15 // 4` → `3`                              |
| `%`              | Modulo (remainder)                 | `17 % 5` → `2`                               |
| `**`             | Exponentiation                     | `2 ** 8` → `256`                             |
| `abs()`          | Absolute value                     | `abs(-42)` → `42`                            |
| `divmod()`       | Returns quotient and remainder     | `divmod(17, 5)` → `(3, 2)`                   |
| `pow()`          | Power with optional modulo         | `pow(2, 10, 1000)` → `24` (2¹⁰ mod 1000)     |
| `bit_length()`   | Number of bits needed to represent | `(1024).bit_length()` → `11`                 |
| `to_bytes()`     | Converts to bytes                  | `(255).to_bytes(2, 'big')` → `b'\x00\xff'`   |
| `from_bytes()`   | Creates int from bytes             | `int.from_bytes(b'\x00\xff', 'big')` → `255` |
| Comparison       | Compare integers                   | `10 > 5` → `True`, `3 == 3` → `True`         |