## Float (`float`) Methods & Operations

| Method/Operation     | Description                        | Usage Example                             |
| -------------------- | ---------------------------------- | ----------------------------------------- |
| `+`, `-`, `*`, `/`   | Basic arithmetic operations        | `3.14 + 2.86` → `6.0`                     |
| `//`                 | Floor division                     | `7.5 // 2.0` → `3.0`                      |
| `%`                  | Modulo operation                   | `7.5 % 2.0` → `1.5`                       |
| `**`                 | Exponentiation                     | `2.5 ** 2` → `6.25`                       |
| `abs()`              | Absolute value                     | `abs(-3.14)` → `3.14`                     |
| `round()`            | Rounds to specified decimal places | `round(3.14159, 2)` → `3.14`              |
| `is_integer()`       | Checks if float is whole number    | `(5.0).is_integer()` → `True`             |
| `as_integer_ratio()` | Returns fraction as tuple          | `(0.25).as_integer_ratio()` → `(1, 4)`    |
| `hex()`              | Returns hex representation         | `(3.14).hex()` → `'0x1.91eb851eb851fp+1'` |
| `fromhex()`          | Creates float from hex string      | `float.fromhex('0x1.8')` → `1.5`          |
| Comparison           | Compare floats                     | `3.14 > 3.0` → `True`                     |
| `math` functions     | Import math for advanced ops       | `import math; math.sqrt(16.0)` → `4.0`    |