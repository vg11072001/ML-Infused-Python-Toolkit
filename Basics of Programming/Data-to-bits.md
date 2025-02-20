
All data we get store in bits format on ram or disk!

 **Understanding Bits**

- A **bit** is the smallest unit of data in a computer and can have one of two values: **0** or **1**.
- Computers use bits because they are based on electronic circuits that can easily represent two states (e.g., on/off, high voltage/low voltage).
- Once a number is converted to binary, it is stored in computer memory as a sequence of bits.
- Memory is organized into **bytes**, where 1 byte = 8 bits.
- For example, the number `13` (`1101` in binary) might be stored in a byte as `00001101`.
- processing:
	- The CPU processes these bits using logic gates and arithmetic circuits.
	- Operations like addition, subtraction, multiplication, and division are performed directly on binary numbers.
- **Images**: Pixels are represented as binary values for color and intensity.
- **Audio**: Sound waves are sampled and quantized into binary values.
## Numbers

### integers: to bits
Numbers are converted into binary (base-2) format, which uses only 0s and 1s. Here's how it works:
**Decimal to Binary Conversion**:

- Divide the number by 2 and record the remainder (0 or 1).
- Repeat the process with the quotient until it becomes 0.
- The binary number is the sequence of remainders read in **reverse** order.
```
13 ÷ 2 = 6 remainder 1
6 ÷ 2 = 3 remainder 0
3 ÷ 2 = 1 remainder 1
1 ÷ 2 = 0 remainder 1
```

- Computers often use a fixed number of bits to represent integers (e.g., 8-bit, 16-bit, 32-bit, 64-bit). - For example, in 8-bit representation, the number `13` would be stored as `00001101`.

### floating-points: to bits
- Floating-point numbers (decimals) are represented using a standard like **IEEE 754**.
- They are split into three parts:
    1. **Sign bit**: Indicates whether the number is positive (0) or negative (1).
    2. **Exponent**: Represents the power of 2 to scale the number.
    3. **Mantissa (Significand)**: Represents the significant digits of the number.
        
    Example: The number `-13.75` in 32-bit floating-point format:
    - Sign bit: `1` (negative)
    - Binary representation of `13.75`: `1101.11`
    - Normalized scientific notation: `1.10111 × 2^3` 
	    - (For `1101.11`, move the binary point to the left until there’s only one digit before the point.  The exponent is **3** because the binary point was moved 3 places to the left.)
    - Exponent: `3` (stored with a bias)  
	    - ` Biased exponent = Actual exponent + Bias
                `= 3 + 127 = 130
        - 130 in binary = 10000010
    - Mantissa: `10111` (stored in the significand field)
	    -  The mantissa is the fractional part of the normalized number (`1.xxxxx`), excluding the leading `1` (since it’s implied).
	    - For `1.10111`, the mantissa is `10111`.
	**Combined**
	```
	Sign bit = 1
	Biased exponent = 10000010
	Mantissa = 10111000000000000000000
    ```



## Characters
- letters, symbols, and other textual data
- Represented using encoding schemes like ASCII or Unicode (e.g., 'A' = `65` in decimal = `01000001` in binary).

### Encoding system of common characters

#### Ascii  **American Standard Code for Information Interchange**:
We have ascii system but limited to use as it define A by American,  
- ASCII is one of the earliest and most widely used encoding schemes.
- It uses **7 bits** to represent each character, allowing for **128 unique characters** (0–127).
- Examples:
    - 'A' = `65` (decimal) = `01000001` (binary)
    - 'a' = `97` (decimal) = `01100001` (binary)
    - '1' = `49` (decimal) = `00110001` (binary)
- ASCII is limited to English letters, digits, punctuation, and control characters.
- each charactar of 1 byte
![](Pasted%20image%2020250220114106.png)
#### **Extended ASCII**
- Extends ASCII to **8 bits**, allowing for **256 unique characters** (0–255).
- The additional 128 characters include symbols, accented letters, and other special characters.
- Example: '€' = `128` (in some extended ASCII versions).

#### Unicode: 
- contain 10k+, more complex than ascii
- grapheme is a single unit of a human writing system,  as they can broken than into letters, 
	- this grapheme can be broken down into  code-points
	- graphene are map to one of code points, each have numerical values, 
	- now code-points to bytes(binary) encoding
##### UTF-8
- code points mapping to
![](Pasted%20image%2020250220114851.png)
UTF-32 take more space ![](Pasted%20image%2020250220114918.png)
![](Pasted%20image%2020250220115051.png)
- code points maps to 1- 4 bytes, 
- code point with lower weights mpas to 1 byte, helps in saving space
- larger values from 2-4
- utf-8 have some in unnormality bcoz each character have different bytes, so indexing in difficult

![](Pasted%20image%2020250220115552.png)![](Pasted%20image%2020250220115624.png)
many lanuuage doesn't interactw ith code point or grapheme only knows a a byte. In string it count the len of character in python returns length of bits, so - example:
![](Pasted%20image%2020250220115942.png)
![](Pasted%20image%2020250220120042.png)
for this string interaction we will need some better library who understand it!

![](Pasted%20image%2020250220122119.png)
ord only take single character means who have single code points
![](Pasted%20image%2020250220122221.png)
![](Pasted%20image%2020250220122343.png)
![](Pasted%20image%2020250220115929.png)

1. To decode bytes into graphemes, we must know the original encoding used.
2. In Unicode, a grapheme != a code point != a byte.
- Use Unicode-unaware functions only if every grapheme is a byte: ASCII or UTF-8 with ASCII characters.
- use Unicode-aware functions to properly handle code points.
- use grapheme-aware functions when maximum accuracy is needed!

## Images
- Pixels are represented as binary values for color and intensity.

## Audio
-  Sound waves are sampled and quantized into binary values.
