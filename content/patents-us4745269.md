---
title: "US Patent 4,745,269 - Dot Code A Barcode Patent"
description: "US Patent 4,745,269 introduced Dot Code A in 1988, pioneering matrix barcode technology with circular dots. Learn about its technical specifications, expiration"
url: "/patents/us4745269.pdf"
date: 2026-06-16
weight: 925
image: "/images/patents-us4745269.jpg"
---

US Patent 4,745,269 represents one of the earliest attempts to encode data in a two-dimensional matrix format using dots rather than traditional bars. Issued on May 17, 1988, to inventors at Veritec Inc., this patent covered a method of identifying objects using an array of circular dots arranged in a specific pattern—a technology that predated modern QR codes and Data Matrix symbols by several years.

## Dot Code A Matrix Encoding Technology

Dot Code A used a rectangular matrix of circular dots where data was encoded through the presence or absence of dots at specific grid positions. Unlike linear barcodes that encode information in the width and spacing of parallel bars, this patent described a system where information density increased dramatically by utilizing both horizontal and vertical space. Each dot position represented a binary value—present dot equals one, absent dot equals zero.

The system employed what the patent called a "position reference pattern"—essentially timing marks that allowed scanners to determine the correct grid alignment and compensate for printing variations. This concept later became standard in nearly all 2D matrix symbologies. Most modern implementations of matrix barcodes owe something to this foundational work, even if they don't directly license the technology.

What made Dot Code A particularly innovative for 1988 was its approach to error correction. The patent described redundancy methods where critical data appeared in multiple locations within the matrix, allowing the system to reconstruct information even when portions of the code were damaged or obscured. Industry data from that era shows failure rates in linear barcodes could exceed 10% in harsh industrial environments—Dot Code A aimed to solve that problem.

## Patent Details and Issuance Date

<a href="https://patents.google.com/patent/US4745269A/en" rel="nofollow">US Patent 4,745,269</a> was filed on August 28, 1986, and granted on May 17, 1988. The inventors listed were Kenneth W. Gunn Jr. and Dwight D. Shepard, both assigned to Veritec Inc., a California-based company that pioneered early 2D barcode technology. The official patent title reads "Method of Identifying Objects Provided with a Code Pattern."

The patent abstract described a method where objects received identification through "a code in the form of a matrix of data cells, each cell being defined by an elemental area on the object and being characterized by the presence or absence of a mark." The filing predated ISO/IEC 16022 (Data Matrix) by more than a decade and appeared years before the standardization efforts that led to modern 2D symbologies we use today.

Veritec positioned this technology as superior to existing linear barcodes for applications requiring high data density in limited space—think small components in electronics manufacturing or pharmaceutical packaging where real estate was precious. The company actively marketed Dot Code A through the late 1980s and early 1990s, though it ultimately lost market share to competing standards like [PDF417 and Data Matrix](/stack.html).

## Matrix of Dots Data Encoding Method

The encoding method described in claim 1 specified a rectangular matrix subdivided into data cells. Each cell contained either a circular dot mark or remained blank. The patent detailed a specific grid structure with finder patterns at corners—similar to what you'd later see in QR codes—that allowed omnidirectional scanning. The scanner could read the code regardless of orientation, a significant advancement over <a href="/39code.html">linear formats like Code 39</a> that required horizontal alignment.

Data capacity varied with matrix size. Typical implementations encoded 50-100 alphanumeric characters in a space roughly equivalent to a postage stamp. The patent claims covered matrices ranging from 10×10 up to 40×40 cells, though practical limits existed based on printing resolution and scanning technology available in the 1980s.

The encoding process converted data through a lookup table that mapped ASCII characters to specific bit patterns distributed across the matrix. Position detection patterns occupied fixed locations at matrix corners, while timing patterns ran along edges. The remaining interior cells stored actual data with error correction codes. This architecture became the template for virtually every matrix symbology developed afterward.

## Patent Expiration Status

Patents issued in 1988 operated under the law effective at that time, which granted protection for 17 years from the issue date. US Patent 4,745,269 therefore entered the public domain on May 17, 2005. Any technology covered by the original claims can now be implemented freely without licensing fees or royalty obligations.

This expiration opened the door for modern implementations of dot-based matrix codes without intellectual property concerns related to this specific patent. However, dozens of subsequent patents refined and extended matrix barcode technology—companies implementing 2D barcodes today need to review the entire patent landscape, not just this foundational document.

The expiration coincided with the rapid adoption of standardized 2D symbologies like Data Matrix (ISO/IEC 16022) and QR Code, which by 2005 had established dominance through standardization bodies and <a href="https://www.gs1.org" rel="nofollow">widespread industry support from organizations like GS1</a>. Dot Code A itself became largely obsolete, though its technical concepts persist in modern implementations.

## Technical Specifications and Claims

The patent contained 23 claims covering various aspects of the encoding and decoding process. Claim 1, the broadest, described the basic method: "A method of identifying an object comprising the steps of: providing on said object a code in the form of a matrix of data cells, each data cell being defined by an elemental area on said object and being characterized by the presence or absence of a mark."

Subsequent claims added specificity around circular dot shapes, minimum size relationships between dots and spacing, error detection through check digits, and the scanner apparatus capable of reading the codes. Claim 18 specifically covered the omnidirectional reading capability, stating the code could be read "independent of the orientation of said object relative to said scanning means."

Technical specifications included:
- Dot diameter: 0.008 to 0.040 inches depending on print resolution
- Cell spacing: 1.5× to 2× dot diameter for reliable detection
- Minimum matrix size: 10×10 cells
- Maximum practical matrix: 40×40 cells
- Print contrast ratio: minimum 20% reflectance difference
- Error correction: up to 30% redundancy in critical data areas

The patent documentation provides fascinating insight into <a href="/history.html">the evolution of barcode technology</a> from strictly linear formats to the two-dimensional codes that now appear on everything from airline boarding passes to pharmaceutical packaging. While Dot Code A didn't achieve the commercial success of later standards, its technical foundation proved sound—modern matrix barcodes use remarkably similar principles of position detection, timing patterns, and error correction first articulated in this 1988 patent.

## Frequently Asked Questions

**Q: Can I use Dot Code A technology without licensing since the patent expired?**

Yes. The patent expired in 2005, placing all technology covered by the original claims into the public domain. However, practical considerations matter more than legal ones—Dot Code A lacks modern standardization, software library support, and scanner availability. Companies implementing 2D barcodes today almost universally choose standardized symbologies like Data Matrix, QR Code, or PDF417, which benefit from ISO/IEC standards, extensive vendor support, and proven interoperability.

**Q: How did Dot Code A compare to modern QR codes?**

Dot Code A preceded QR codes by several years and established many foundational concepts—matrix structure, position detection patterns, and omnidirectional reading. However, QR codes (developed by Denso Wave in 1994) incorporated more sophisticated error correction using Reed-Solomon algorithms, achieved higher data density, and benefited from Japanese Industrial Standards (JIS) and later ISO/IEC 18004 standardization. QR codes also optimized for rapid scanning—hence "Quick Response"—through better position detection patterns. Dot Code A was innovative for its era but couldn't compete once standardized alternatives emerged with broader industry backing.

**Q: Why didn't Dot Code A achieve widespread adoption?**

Three factors limited adoption: proprietary nature, timing, and competition. Veritec controlled the technology through patents and required licensing, creating friction for potential adopters. The technology emerged before international standardization bodies established formal processes for 2D symbologies. Finally, competing technologies like PDF417 (Symbol Technologies, 1991) and Data Matrix (RVSI Acuity CiMatrix, mid-1990s) offered better technical specifications and pursued open standardization, making them more attractive for large-scale implementations across supply chains requiring interoperability.

---