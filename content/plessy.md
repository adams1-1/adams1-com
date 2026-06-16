---
title: "Plessey Barcode - Specification and Implementation"
description: "Complete technical guide to Plessey barcode symbology, covering encoding structure, CRC verification, legacy implementations in libraries and retail, and practi"
slug: "plessy"
date: 2026-06-16
weight: 962
image: "/images/plessy.jpg"
---

# Plessey Barcode - Specification and Implementation

Plessey barcode is a continuous, variable-length symbology developed in the 1970s by the Plessey Company for use in library management and retail applications. While largely superseded by more modern symbologies, understanding Plessey remains relevant for legacy system maintenance and historical barcode implementations that still exist in specialized environments.

## Plessey Barcode Symbology Overview

The Plessey barcode system, also known as Plessey Code, emerged from British defense contractor Plessey Company's need for a tracking system. Unlike UPC or EAN codes designed for consumer products, Plessey targeted industrial and institutional applications where continuous reading of variable-length numeric data was essential.

The symbology encodes numeric data (0-9) plus hexadecimal characters A-F in some variants, though pure numeric implementation dominates actual deployments. Each character consists of four bars, making it a pulse-width modulated code where both bar and space widths carry information. This differs fundamentally from <a href="/39code.html">Code 39's discrete structure</a> where only bars encode data.

Plessey's continuous nature means no inter-character gaps — bars and spaces flow without interruption from start to end. This design choice improved scanning reliability on early optical equipment but created implementation challenges that contributed to its eventual replacement by <a href="/128code.html">Code 128</a> in most applications.

The symbology includes a mandatory cyclic redundancy check (CRC) for error detection, calculated using a modulo-11 algorithm on the numeric data string. This error-checking mechanism was sophisticated for its era, though modern symbologies employ more advanced verification methods.

## Character Encoding Structure

Plessey uses a 4-unit encoding pattern where each character requires exactly four bars with varying widths. The encoding follows a binary pulse-width scheme: narrow elements represent binary 0, wide elements represent binary 1. Each character encodes to a specific 4-bit binary pattern.

The numeric digits map as follows: the decimal value converts to binary, then each bit determines bar width. For example, digit 5 (binary 0101) encodes as narrow-wide-narrow-wide. The spaces between bars follow the inverse pattern, creating a continuous waveform.

Start and stop patterns use distinct sequences. The start code consists of D (1101 binary), while stop patterns vary by implementation — some use FD (reverse start), others employ different termination sequences. This inconsistency across implementations represents one of Plessey's practical weaknesses.

Check digit calculation applies modulo-11 mathematics to the data string. Each digit position receives a weight, multiplied by the digit value, summed, then divided by 11. The remainder determines the check digit. Some implementations append a second check digit using modulo-7 calculation for enhanced error detection, though this wasn't universally adopted.

The bit-level encoding creates density limitations. Plessey requires approximately 0.01 inches per character at typical print resolutions, making it less space-efficient than modern high-density symbologies. Each character needs 8 modules minimum (4 bars, 4 spaces), plus the overhead of start/stop patterns and check digits.

## Applications in Retail and Libraries

Library systems represented Plessey's primary deployment environment through the 1980s and 1990s. British and European libraries particularly favored Plessey for book tracking, patron cards, and inventory management. The continuous symbology proved reliable for damaged or worn labels — partial reads could still succeed where discrete symbologies failed completely.

Retail applications focused on price marking and shelf labels rather than point-of-sale scanning. Grocery chains in the UK used Plessey for internal inventory before <a href="https://en.wikipedia.org/wiki/Universal_Product_Code" rel="nofollow">UPC adoption</a> became mandatory for consumer products. The symbology's variable length accommodated product codes of different sizes without padding.

Warehousing operations adopted Plessey for pallet tracking and location management. The symbology's tolerance for label damage and its readability under varying lighting conditions suited industrial environments. However, the numeric-only limitation restricted complex inventory systems that needed alphanumeric capability.

Most deployments you'll encounter today are legacy systems requiring maintenance rather than new implementations. Converting these systems to contemporary standards like GS1-128 often proves cost-prohibitive for organizations with thousands of existing labeled items. I've personally seen facilities with 50,000+ Plessey-labeled items where migration costs exceed $200,000.

One interesting application persists in specialized access control systems where Plessey badges from the 1980s remain in use. Replacing these systems requires hardware upgrades across entire facilities — a capital expense many institutions defer indefinitely. A university in Manchester still operates their original 1987 Plessey access control system across 42 buildings.

## Technical Specifications

Plessey operates as a bidirectional symbology, readable in either scanning direction. The decoder determines orientation from the start/stop pattern relationship. This bidirectionality simplified early scanning equipment design but required more complex decoding algorithms.

Bar width ratios follow a 2:1 or 3:1 narrow-to-wide specification depending on implementation. The 2:1 ratio produces denser codes but demands tighter print tolerances. Industrial applications typically specified 3:1 ratios for improved first-read rates on lower-quality printing equipment.

Module width (X-dimension) typically ranges from 0.0075 to 0.030 inches, though 0.010 inches represents the practical minimum for reliable reading. Quiet zones require 10X minimum on each side — significantly larger than modern symbology requirements. This generous quiet zone compensated for early scanner optics with limited depth of field.

Print quality specifications demand edge roughness below 0.15 X-dimension and spot diameter less than 0.3 X-dimension. These tight tolerances reflected Plessey's era before adaptive decoding algorithms could compensate for print defects. Modern scanners handle degraded Plessey codes better than the original readers for which the symbology was designed.

Height specifications are non-critical — most implementations use 0.5 to 1.0 inch tall bars. Unlike Code 128 where height affects reading performance, Plessey's continuous structure tolerates shorter bars without significant decode failure.

The symbology lacks any inherent data capacity specification — variable length accommodates whatever string length the application requires, limited only by practical label size and reading distance constraints. Most implementations stayed below 20 characters to maintain reasonable label dimensions.

## Implementation Examples

Hardware implementation requires understanding Plessey's variants. MSI Plessey (developed by MSI Data Corporation) became the dominant North American variant, incorporating modified check digit algorithms. European implementations often used the original Plessey specification with different termination patterns.

Print generation for Plessey demands precise timing control. Software must calculate exact bar widths based on the chosen narrow-to-wide ratio and X-dimension. Most modern barcode generation libraries include Plessey support primarily for legacy compatibility rather than new deployments.

A typical implementation sequence:
1. Encode the data string to binary patterns
2. Calculate the modulo-11 check digit
3. Append start pattern (D hexadecimal)
4. Generate bar/space sequence following binary encoding
5. Append check digit encoding
6. Add stop pattern (FD or implementation-specific)
7. Add required quiet zones

Scanner configuration for Plessey reading often requires enabling the symbology explicitly — most modern scanners disable Plessey by default since it's rarely encountered in current commerce. Verification scans should test both reading directions and various positions within the scanner's field of view.

Integration with modern systems presents challenges. Contemporary databases expect alphanumeric identifiers, while Plessey delivers numeric strings. Middleware translation layers become necessary, mapping Plessey numeric codes to modern SKU or tracking number formats.

## Frequently Asked Questions

**Q: Can Plessey barcodes encode letters and symbols or only numbers?**

Pure Plessey specification encodes hexadecimal characters (0-9 and A-F), though most implementations restrict input to numeric digits 0-9. The symbology cannot encode lowercase letters, punctuation, or special characters. If your application requires full alphanumeric capability, Code 128 provides better functionality and broader scanner support. MSI Plessey variants typically enforce numeric-only encoding even more strictly than the original specification.

**Q: Why are Plessey barcodes rarely used in new implementations today?**

Plessey lacks the data density, character set flexibility, and standardization that modern supply chains require. Code 128 offers superior density with full ASCII support, while GS1-128 adds application identifier structure for complex data. Additionally, <a href="https://www.gs1.org/standards/barcodes" rel="nofollow">GS1 standards</a> don't include Plessey in their recommended symbologies, effectively excluding it from global commerce. The symbology survives only in legacy systems where replacement costs exceed the operational benefits of migration to contemporary standards.

**Q: How do MSI Plessey and original Plessey differ?**

MSI Plessey modified the original specification primarily in check digit calculation and stop pattern definition. MSI variants typically use modulo-10 check digits instead of modulo-11, and some implementations include dual check digits. The start/stop patterns also differ between variants, causing cross-compatibility issues. When maintaining legacy systems, you must identify which specific Plessey variant the original implementation used — assumptions about "standard" Plessey often lead to decode failures.