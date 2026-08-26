---
title: "Code 128 Barcode - High Density Alphanumeric Standard"
description: "Code 128 barcode technical guide: character sets A/B/C, function codes, implementation examples, and why it encodes 37% more efficiently than alternatives in sh"
url: "/128code.html"
date: 2026-07-13
weight: 907
image: "/images/128code.jpg"
---

Code 128 remains the dominant high-density linear barcode in logistics and manufacturing because it efficiently encodes the full 128-character ASCII set in minimal space. Developed by Computer Identics Corporation in 1981, this symbology delivers variable-length alphanumeric encoding with built-in error checking — capabilities that UPC and Code 39 simply can't match. If your application requires letters, numbers, and control characters in a compact format, Code 128 is the standard.

## Code 128 Symbology Overview

Code 128 defines 106 distinct symbol patterns, each representing different data values depending on the active character set. The symbology uses four bar-element widths (1X to 4X modules) arranged in three bars and three spaces per character. Every symbol contains 11 modules total, maintaining consistent density regardless of data content.

The structure follows this pattern: start character, one or more data characters, mandatory modulo-103 check digit, and stop character with termination bar. Total symbol width equals: (11C + 35) modules, where C represents the character count including start, check, and code set characters.

According to <a href="https://www.iso.org/standard/65502.html" rel="nofollow">ISO/IEC 15417 specifications</a>, minimum X-dimension measures 0.191mm (7.5 mils), though most industrial implementations use 0.25mm or larger for reliable scanning. The quiet zone requires 10X modules on each side — non-negotiable for proper decode.

Automatic character set switching makes Code 128 practical. The encoder selects the optimal subset for each data segment, minimizing overall symbol length. A numeric-only sequence uses subset C (double-density mode), while mixed alphanumeric content triggers subset B. This flexibility typically generates symbols 20-30% shorter than Code 39 for equivalent data.

## Character Sets and Subsets (A, B, C)

Code 128 operates through three character sets that share the same 106 bar patterns but assign different meanings to each pattern. Think of them as three lookup tables using one physical symbol set.

**Subset A** encodes uppercase letters, digits, punctuation, and ASCII control characters 00-31. This subset handles industrial control applications requiring device communication codes like STX, ETX, or ACK. Most retail or shipping applications never touch subset A — it's specialized territory.

**Subset B** covers uppercase and lowercase letters, digits, and standard punctuation — essentially ASCII characters 32-127. This is the workhorse subset for general alphanumeric data. Product descriptions, serial numbers, and human-readable identifiers live here.

**Subset C** is where Code 128 shows its efficiency advantage. This subset encodes numeric pairs (00-99) in a single symbol character, effectively doubling density for numeric data. Shipping container codes, case identifiers, and serial shipping container codes (SSCCs) use subset C for compact encoding. A 14-digit GTIN requires only 7 symbol characters in subset C versus 14 in subset B.

The encoder automatically shifts between subsets using dedicated shift and code change characters. A symbol starting "ABC123456789XYZ" would typically begin in subset B for letters, switch to subset C for the numeric string (using just 5 characters instead of 10), then shift back to B for the final letters. The decoder handles these transitions transparently.

Character value 95 in subset A represents FNC1, while the same bar pattern means underscore in subset B and FNC1 in subset C. The active subset at any position determines interpretation — this is why proper encoding matters.

## Start Characters and Symbol Patterns

Every Code 128 symbol begins with one of three start characters: Start A, Start B, or Start C. These patterns serve dual purposes: they signal the beginning of the barcode and establish the initial active character set. The scanner reads this first pattern to synchronize timing and determine which lookup table to apply.

The start character pattern uses a unique 11-module arrangement (2-1-1-3-1-2 for Start B, as an example) that cannot occur elsewhere in the symbol. This prevents mid-symbol false reads and establishes directionality — Code 128 is bidirectionally scannable, meaning it decodes correctly from either direction.

Each of the 106 symbol patterns consists of three bars (black) and three spaces (white) totaling exactly 11 modules. Pattern values follow the formula: (11a + 8b + 5c + 2d - 3), where a, b, c, d represent the four element widths reading left to right (bars and spaces alternating). This mathematical relationship creates the balanced structure that enables reliable high-speed scanning.

The <a href="/128table.html">Code 128 character table</a> shows all 106 patterns with their corresponding values in subsets A, B, and C. Bar widths range from 1 to 4 modules, but the total never exceeds 11 — maintaining constant character density regardless of data content.

Stop pattern (2-3-3-1-1-1-2) includes a unique 13-module structure with termination bar. That final 2-module bar provides the scanner with definitive symbol end detection. Some implementations incorrectly omit the termination bar, creating decode failures on certain scanner models.

## Function Codes (FNC1, FNC2, FNC3, FNC4)

Function codes embed control information within the data stream without consuming space for printable characters. These special codes differentiate Code 128 from simpler symbologies and enable sophisticated applications like <a href="/ucc128.html">UCC/EAN-128 application identifiers</a>.

**FNC1** in the first position (immediately after the start character) designates the symbol as a GS1-128 barcode, indicating that data follows GS1 Application Identifier formatting rules. FNC1 in any other position serves as a field separator, equivalent to ASCII Group Separator (GS). Shipping labels use FNC1 to delimit variable-length fields like batch numbers or expiration dates within a single barcode. Without FNC1 separators, parsers can't determine where one field ends and the next begins in variable-length data structures.

**FNC2** indicates the symbol contains a message append identifier, signaling that this barcode is part of a multi-symbol sequence. The following data specifies position information allowing the decoder to reassemble fragmented messages. This function sees limited deployment outside specialized industrial applications where data exceeds practical single-symbol capacity.

**FNC3** remains largely unused in modern implementations. Originally intended for initialization procedures in certain readers, most current scanners ignore FNC3 entirely. Consider it a legacy placeholder.

**FNC4** extends character set capabilities by modifying the interpretation of the following character. In subset A or B, FNC4 provides access to extended ASCII characters outside the standard range. Subset C doesn't use FNC4 since it only encodes numeric pairs. Real-world applications rarely employ FNC4 — standard ASCII covers most practical requirements, and Unicode support requires 2D symbologies anyway.

The modulo-103 check digit calculation includes function codes as their respective character values (102 for FNC1, 97 for FNC2, etc.). Omitting function codes from check digit calculation is a common encoder implementation error that produces technically valid-looking but specification-violating symbols.

## Implementation Guide and Examples

Starting implementation requires three decisions: character subset selection, function code requirements, and physical dimensions. For numeric-only data like "12345678", start with Code C and encode as four symbol characters (12, 34, 56, 78) plus start, check, and stop — seven total characters occupying 112 modules. The same data in subset B would require 13 characters and 178 modules. That's 37% longer for identical information.

Mixed alphanumeric content like "SHIP-001-20231215" benefits from multi-subset encoding: start B for "SHIP-", maintain B for "001-" (the hyphen requires subset B), then shift to C for date "20231215" encoded as four character pairs (20, 23, 12, 15). Total symbol: approximately 165 modules versus 220 for pure subset B encoding.

**GS1-128 example for GTIN + expiration date:**
- Data: (01)00012345678905(17)231215
- Encoding: Start C, FNC1, 01, 00, 01, 23, 45, 67, 89, 05, 17, 23, 12, 15, check digit, stop
- The FNC1 in first position declares GS1 formatting; AI (01) and (17) are encoded directly as numeric pairs

Print quality directly impacts scan reliability. Ink spread (gain) increases bar widths, effectively reducing space widths and creating asymmetric elements. Specify 0.5mm X-dimension when printing on corrugated packaging — smaller dimensions invite decode failures from substrate roughness and printing variability. Industrial thermal transfer printers deliver consistent results; inkjet and laser printers on plain paper require testing and potential X-dimension increases.

Verification requires an ISO/IEC 15416-compliant scanner measuring parameters like modulation, edge contrast, and decode. A barcode that "scans" isn't necessarily specification-compliant. I've seen countless implementations where barcode decodes successfully but fails ISO grading due to inadequate quiet zones or inconsistent element widths. These symbols work until they don't — usually during high-speed conveyor scanning or at oblique angles.

Free encoding resources exist, but verify output against the <a href="https://www.gs1.org/standards/barcodes/application-identifiers" rel="nofollow">GS1 barcode standards</a> before production deployment. Many online generators produce technically incorrect symbols that happen to work with forgiving scanners, creating fragile implementations that fail under stress.

## Frequently Asked Questions

**Q: Can Code 128 encode lowercase letters and special characters?**

Yes, subset B provides full uppercase, lowercase, and standard ASCII punctuation (characters 32-127). This includes brackets, parentheses, math operators, and common symbols. For control characters like carriage return or tab, use subset A. Code 128 cannot natively encode Unicode or extended characters above ASCII 127 — those require 2D symbologies like <a href="/stack.html">Data Matrix or QR codes</a>.

**Q: What's the maximum data capacity for Code 128?**

Theoretically unlimited, but practical constraints apply. Most scanner buffers handle 48-64 characters comfortably. Beyond 80 characters, symbol length creates printing and scanning challenges — the barcode becomes physically unwieldy and susceptible to damage or distortion. Applications requiring more data should consider 2D barcode formats that pack information vertically rather than extending horizontally. For comparison, Code 39 typically maxes out around 40 characters before becoming impractical.

**Q: Does Code 128 require specific printing technology?**

No specific technology is mandatory, but print quality matters significantly. Thermal transfer and direct thermal printers deliver excellent results with consistent edge definition. Laser printers work for office applications but verify X-dimension accuracy — some models introduce slight dimensional errors. Inkjet printing requires high-quality settings and ink spread compensation. The symbology works with any printing method that maintains dimensional accuracy within ±10% and provides adequate edge sharpness for the chosen X-dimension.