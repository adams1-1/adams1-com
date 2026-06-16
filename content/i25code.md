---
title: "Interleaved 2 of 5 Barcode - Specification & Guide"
description: "Interleaved 2 of 5 (ITF) is a high-density numeric barcode that encodes digit pairs by interleaving bars and spaces. Learn about ITF-14 structure, encoding meth"
slug: "i25code"
date: 2026-06-16
weight: 937
image: "/images/i25code.jpg"
---

Interleaved 2 of 5 (ITF) is a high-density numeric barcode symbology that encodes digit pairs by interleaving bars and spaces, making it roughly twice as efficient as standard 2 of 5 formats. Developed by Intermec Corporation in the 1970s, ITF became the foundation for the ITF-14 standard used globally on corrugated shipping containers. This symbology requires an even number of digits and provides excellent print tolerance, which is why it remains the dominant choice for logistics despite being nearly 50 years old.

## Interleaved 2 of 5 Symbology Overview

The design of Interleaved 2 of 5 centers on its encoding method: each digit pair creates a single pattern where the first digit forms the bars and the second digit forms the intervening spaces. This interleaving approach reduces the physical width required compared to encoding each digit separately, achieving densities of approximately 17.8 characters per inch at common print resolutions.

The symbology uses only two element widths—narrow and wide—with a ratio typically between 2:1 and 3:1. Five elements (either bars or spaces) represent each digit, with exactly two of those five elements being wide. This "2 of 5" naming convention describes the fundamental encoding rule that makes the code self-checking.

ITF supports only numeric digits 0-9, making it unsuitable for applications requiring letters or special characters. The code requires a start pattern (four narrow elements), data character pairs, and a stop pattern (one wide bar, one narrow bar, one narrow space). Optional check digits can be calculated using modulo 10 algorithms, though many implementations skip this since the interleaving provides inherent error detection.

## Character Encoding and Structure

Each digit in ITF uses a specific five-element pattern drawn from only ten possible combinations. The digit 0 uses pattern NNWWN (narrow-narrow-wide-wide-narrow), while 9 uses WNNWN. When interleaving two digits, the decoder alternates reading bars and spaces to extract both values from a single composite pattern.

For example, encoding the digit pair "12" creates a pattern where 1's bar pattern (WNNWN) interleaves with 2's space pattern (NNWWN). The physical barcode shows: wide bar, narrow space, narrow bar, narrow space, narrow bar, wide space, wide bar, wide space, narrow bar, narrow space. Scanners decode by separating odd-positioned elements (bars) from even-positioned elements (spaces).

The start pattern consists of four consecutive narrow elements (NNNN), always rendered as narrow bar, narrow space, narrow bar, narrow space. This distinctive opening alerts decoders that an ITF symbol follows. The stop pattern reverses this logic with wide bar, narrow bar, narrow space—providing clear boundaries for bidirectional scanning.

Check digit calculation follows the standard modulo 10 weighted algorithm: sum odd-position digits multiplied by 3, add even-position digits, subtract from next multiple of 10. The ITF-14 variant <a href="https://www.gs1.org/standards/barcodes/ean-upc" rel="nofollow">mandated by GS1</a> always includes this check digit as the 14th character, ensuring data integrity across global supply chains.

## Numeric-Only Barcode Standard

The numeric-only limitation stems from ITF's binary element width system—with only two widths and five positions per digit, the mathematics support exactly ten unique patterns. Expanding to alphanumeric characters would require additional element widths or positions, destroying the high-density advantage that makes ITF valuable.

This constraint matters less than you'd think. Shipping containers, pallets, and master cartons rarely need alphabetic identifiers at the unit level. The [Code 128 barcode](/128code.html) handles alphanumeric requirements for item-level tracking, while ITF dominates outer packaging where numeric Global Trade Item Numbers (GTINs) suffice.

The even-digit requirement occasionally trips up implementers. ITF physically cannot encode odd-length data—attempting to encode "12345" fails because the fifth digit has no partner for interleaving. Standard practice prepends a leading zero, converting "12345" to "012345" before encoding. Some decoders automatically strip this padding; others preserve it, so applications must handle both scenarios.

Maximum data capacity varies by implementation, but practical limits fall around 30-40 digits before barcode width becomes problematic. Most ITF usage stays well below this threshold—ITF-14 uses exactly 14 digits, distribution codes use 12-16, and carton serial numbers rarely exceed 20 digits even in high-volume pharmaceutical applications.

## Applications in Logistics and Warehousing

ITF-14 revolutionized pallet and carton tracking when GS1 standardized it in the 1980s. The format encodes a 14-digit GTIN with a bearer bar—a continuous rectangular border surrounding the barcode that improves scanning reliability on corrugated cardboard. This bearer bar prevents partial scans when the substrate flexes during conveyor transport, a problem that plagued earlier symbologies.

Warehousing operations prefer ITF because it prints reliably using low-resolution methods like flexographic printing directly onto corrugated material. Unlike <a href="https://en.wikipedia.org/wiki/Universal_Product_Code" rel="nofollow">UPC codes</a> requiring precise registration, ITF tolerates ink spread, uneven surfaces, and damaged edges. The wide tolerances specified in ISO/IEC 16390 permit successful scanning even when 30% of the barcode is damaged or obscured.

Distribution centers use ITF for license plate tracking—unique identifiers assigned to pallets moving through cross-dock operations. These 18-20 digit codes combine shipper ID, date codes, and sequential numbers without requiring database lookups at every scan point. The self-contained numeric data enables offline scanning during network outages, a critical capability for 24/7 logistics operations.

Pharmaceutical serialization increasingly combines ITF-14 on outer packaging with 2D barcodes on individual units. The ITF code provides rapid conveyor scanning for case-level tracking, while DataMatrix codes on bottles carry detailed lot and expiration data. This dual approach balances speed requirements (300+ cases per minute) with regulatory compliance mandating unit-level serialization.

## Complete Specification and Examples

The ITF specification defines several critical parameters that implementers must follow. The nominal X-dimension (narrow element width) ranges from 0.495mm to 1.016mm, with larger dimensions preferred for low-resolution printing. The wide-to-narrow ratio must fall between 2.0:1 and 3.0:1—most implementations use 2.5:1 as a practical compromise between density and print tolerance.

Quiet zones require at least 10X before the start pattern and 10X after the stop pattern, where X equals the narrow element width. For a barcode with 0.5mm narrow elements, this translates to 5mm clear space on each side. Inadequate quiet zones cause scan failures when adjacent graphics or text confuse the decoder's pattern recognition.

Bearer bars add horizontal lines above and below the barcode, connecting the left and right quiet zones into a complete rectangular frame. The bar width should equal twice the narrow element width. While optional in generic ITF, bearer bars are mandatory for ITF-14 per GS1 specifications. They dramatically improve scan reliability on low-contrast substrates by creating clear boundary detection for imaging scanners.

Here's a practical encoding example for the GTIN "01234567890128" (ITF-14 format):
- Leading digit: 0
- Company prefix: 123456
- Item reference: 78901
- Check digit: 2 (calculated via modulo 10)
- Encoded pairs: 01, 23, 45, 67, 89, 01, 28

The physical symbol would span approximately 142mm at the minimum X-dimension, plus quiet zones. Most corrugated applications print at 0.75-1.0mm X-dimensions, producing barcodes 200-250mm wide—easily accommodated on standard shipping cases while remaining scannable from distances up to 50cm.

For historical context on how mechanical scanners evolved into [modern imaging systems](/history.html), the development timeline shows how damaged or partially obscured codes became readable through algorithmic improvements.

## Frequently Asked Questions

**Q: Can Interleaved 2 of 5 encode alphabetic characters?**

No. The symbology's structure mathematically limits it to ten unique patterns representing digits 0-9. The five-element, two-width encoding system cannot expand to accommodate 26 letters without adding element positions or additional widths, which would eliminate the density advantage. For alphanumeric data, use Code 128 or Code 39 instead—ITF exists specifically for numeric applications where its compact size and print tolerance matter most.

**Q: Why does ITF-14 require exactly 14 digits?**

The 14-digit requirement aligns with GS1's Global Trade Item Number structure: one packaging level indicator digit, company prefix (7-10 digits), item reference (remaining digits), and one check digit totaling 14. This standardization enables worldwide interoperability without database lookups. The even-digit count naturally fits ITF's pair-based encoding, and 14 digits provide enough namespace for billions of unique product identifiers while keeping barcode width manageable on shipping containers.

**Q: What's the difference between ITF and Standard 2 of 5?**

Standard 2 of 5 (also called Industrial 2 of 5) encodes each digit separately using bars only—spaces serve merely as separators. ITF interleaves digit pairs by encoding one digit in the bars and the partner digit in the spaces, essentially cutting the symbol length in half. This makes ITF roughly twice as dense. Standard 2 of 5 saw limited adoption and is now obsolete in most industries, while ITF remains the global standard for corrugated packaging identification.