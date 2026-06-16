---
title: "Code 128 Character Table - 106 Symbol Patterns Index"
description: "Code 128 uses 106 symbol patterns to encode data across three character subsets (A, B, C). Learn how the complete character set, function codes, and start chara"
url: "/128table.html"
date: 2026-06-16
weight: 947
image: "/images/128table.jpg"
---

Code 128 uses exactly 106 different symbol patterns to encode data, with each pattern representing a unique value across three character subsets (A, B, and C). The symbology includes 103 data characters, three start characters, and one stop pattern, making it one of the most versatile linear barcodes for alphanumeric and numeric data.

## Complete Code 128 Character Set Reference

The [Code 128 barcode standard](/128code.html) defines 107 total symbol patterns, but only 106 are used during normal encoding operations. Each pattern consists of 11 modules (bars and spaces) arranged in three bars and three spaces. The width of each element ranges from 1 to 4 modules, and every pattern maintains a total width of exactly 11 modules.

The character set divides into three subsets that share the same physical patterns but interpret them differently:

**Subset A** encodes uppercase letters, digits, control characters (ASCII 00-95), and four function codes. This subset handles legacy applications requiring control characters like carriage return and line feed.

**Subset B** encodes uppercase and lowercase letters, digits, and ASCII characters 32-127. Most modern applications use Subset B because it covers standard printable characters including lowercase letters.

**Subset C** encodes digit pairs as single characters, representing values 00 through 99. This doubles encoding density for numeric data — shipping container codes and serial numbers benefit significantly from this compression.

Each of the 103 data values has three different meanings depending on which subset is active. Value 65 represents "A" in Subset A, "a" in Subset B, or the number pair "65" in Subset C. The decoder tracks subset state throughout the symbol to interpret patterns correctly.

## 106 Different Symbol Patterns Explained

Here's where Code 128 gets technically interesting: the symbology defines 107 distinct bar-space patterns, but pattern 106 serves exclusively as the stop character. During data encoding, only patterns 0-105 are available, giving us the "106 different symbol patterns" used for data representation.

Each pattern represents a unique 11-module sequence. Pattern 0 consists of bar-space-bar-space-bar-space with widths 2-1-2-2-2-2. Pattern 105 uses widths 2-3-3-1-1-1-2. The <a href="https://en.wikipedia.org/wiki/Code_128" rel="nofollow">ISO/IEC 15417 standard</a> documents every pattern's exact module arrangement.

The stop pattern (107) differs from data patterns — it spans 13 modules instead of 11, ending with a 2-module wide termination bar. This unique structure signals the scanner that symbol decoding is complete.

Why 106 patterns instead of a power of 2 like 128? Because Code 128's design prioritizes practical encoding needs over mathematical elegance. The 103 data values plus three start codes plus stop pattern equals exactly what's needed for alphanumeric encoding with multiple subset switching capabilities.

Value assignment follows a logical structure. Values 0-99 map directly to digit pairs in Subset C. Values 64-95 in Subset A correspond to ASCII control characters. Values 32-95 represent identical printable characters in both Subset A and Subset B, allowing seamless switching for these common characters.

## Function Character Codes (FNC1: 102, FNC3: 96)

Code 128 includes four function characters that control special behaviors without representing data. These occupy specific value positions in the character table:

**FNC1 (value 102)** has two distinct uses depending on position. When FNC1 appears immediately after the start character, it designates the symbol as a GS1-128 barcode, triggering Application Identifier parsing rules. According to <a href="https://www.gs1.org/standards/barcodes/application-identifiers" rel="nofollow">GS1 specifications</a>, this transforms Code 128 into a supply chain standard capable of encoding product identification, batch numbers, and expiration dates in a single symbol.

When FNC1 appears elsewhere in the data, it acts as a field separator in GS1-128 symbols or remains inactive in standard Code 128 symbols. Most scanning software ignores mid-symbol FNC1 unless GS1 mode is active.

**FNC2 (value 93)** instructs the decoder to buffer the next character for message appending. Multiple symbols on the same label can link together using FNC2. Honestly, most implementations ignore this function — I've seen it used maybe twice in production environments.

**FNC3 (value 96)** triggers extended channel interpretation, allowing Code 128 to reference 256 different data channels beyond standard ASCII. Industry applications rarely implement this capability. I encountered exactly one production system using FNC3 in 20 years — a pharmaceutical tracking application that needed to embed binary sensor data in linear barcodes.

**FNC4 (values vary by subset)** provides extended ASCII access in Subsets A and B, allowing characters 128-255 to be encoded by prefixing standard characters with FNC4. Value assignments: 101 in Subset A, 100 in Subset B.

## Start Character Variations

Code 128 requires one of three start characters, each activating a different initial subset. This design choice eliminates the need for a subset selection character at the beginning of data.

**Start A (value 103)** initializes Subset A. Use this when the first data character is a control character or when uppercase-only text begins the encoded data. Pattern: 2-1-1-4-1-2 module widths.

**Start B (value 104)** initializes Subset B. Modern applications default to Start B for mixed-case alphanumeric data. Pattern: 2-1-1-2-1-4 module widths. This is the most commonly used start character in contemporary implementations.

**Start C (value 105)** initializes Subset C for numeric encoding. [UCC/EAN-128 shipping labels](/ucc128.html) frequently use Start C because container codes, weights, and dates are predominantly numeric. Pattern: 2-1-1-2-3-2 module widths.

The start character directly affects encoding efficiency. A serial number "12345ABC" encodes more efficiently as Start C (digit pairs 12, 34) + Code B + "5ABC" than as Start B for the entire string. Optimal encoders analyze data content to select the best start character and minimize subset switches.

## Character Subset Encoding Tables

Complete encoding tables map each value (0-105) to its interpretation in all three subsets:

**Values 0-9** represent digits across all subsets. In Subset C, these combine as pairs: value 0 encodes "00", value 9 encodes "09".

**Values 10-31** in Subsets A/B encode digits and punctuation. In Subset C, these represent digit pairs "10" through "31".

**Values 32-95** maintain identical assignments in Subsets A and B (space through underscore in ASCII). Subset C continues digit pair encoding through "95".

**Values 96-99** encode special characters in A/B, digit pairs "96"-"99" in Subset C.

**Values 100-105** contain function codes and subset shift commands. Code A (value 101 in B, 100 in C) switches to Subset A. Code B (value 100 in A, 101 in C) switches to Subset B. Code C (value 99 in A/B) switches to Subset C. Shift (value 98 in A/B) temporarily accesses the opposite A/B subset for one character only.

The modulo 103 check digit uses the same value table. Each character's value multiplies by its position (start character = position 1), sum the products, divide by 103, and encode the remainder as the check character. The [barcode implementation guide](/pub) provides detailed check digit calculation examples.

This encoding flexibility explains why Code 128 replaced earlier symbologies like [Code 39](/39code.html) in high-density applications. A typical shipping label might start in Subset C for numeric container codes, switch to Subset B for product descriptions, and return to Subset C for weight values — all within a single compact symbol.

## Frequently Asked Questions

**Q: Why does Code 128 use 106 patterns instead of 128 like the name suggests?**

The name "Code 128" refers to the 128 ASCII characters the symbology can encode, not the number of bar patterns. The actual implementation uses 107 total patterns (106 for data/control + 1 stop pattern) because this provides exactly what's needed for three character subsets, function codes, and control operations. The number 128 is marketing-friendly and indicates ASCII compatibility, but the technical structure prioritizes encoding efficiency over matching the name numerically.

**Q: How do I know which subset to use for encoding data?**

Start with Subset B for mixed-case alphanumeric text — it handles 95% of common encoding needs. Use Subset C when encoding six or more consecutive digits (each pair encodes as one character, cutting symbol length roughly in half). Subset A appears mainly in legacy systems requiring control characters. Modern encoding software automatically selects optimal subsets and switch points based on data analysis. For manual encoding, count character types in your data and calculate symbol length for each subset combination — shortest result wins.

**Q: What does value 102 (FNC1) actually do in a Code 128 barcode?**

FNC1 at position 1 (right after the start character) converts Code 128 into GS1-128 format, enabling Application Identifier parsing for supply chain data like expiration dates and batch numbers. FNC1 elsewhere in GS1-128 symbols acts as a variable-length field separator. In standard Code 128 (non-GS1), FNC1 typically gets ignored by decoders. Think of first-position FNC1 as a mode switch that completely changes how the following data is interpreted — without it, scanners read the raw character stream; with it, they parse structured GS1 data fields.