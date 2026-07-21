---
title: "BarCode 1 Updates - What's New in Barcode Technology"
description: "BarCode 1 site updates include new 2D barcode specifications, GS1 Digital Link documentation, and programming examples for Python, JavaScript, and Go. Latest IS"
url: "/new.html"
date: 2026-07-13
weight: 943
image: "/images/new.jpg"
---

BarCode 1 has served the industry since the early days of the commercial internet, and we're constantly updating our technical resources to match the evolving standards landscape. Recent additions include expanded 2D barcode specifications, updated GS1 application identifier tables, and new programming examples for modern development environments. Here's what's changed and what's coming next.

## Latest Updates to BarCode 1 Site

The core specification pages have received substantial updates. Our [Code 128 reference](/128code.html) now includes complete character set tables aligned with ISO/IEC 15417:2007, plus implementation notes for the three subset variations (A, B, and C). The UPC/EAN documentation has been expanded to cover the 2027 transition requirements — GS1 mandates that retail systems must accept <a href="https://www.gs1.org/standards/gs1-datamatrix" rel="nofollow">GS1 DataMatrix codes</a> alongside traditional linear barcodes starting in three years.

We've reorganized the [barcode information resources](/pub) section to separate legacy specifications from current standards. PDF downloads of original patents remain available for historical reference, but active implementation pages now link directly to the controlling standards bodies. This matters because many "authoritative" barcode sites still reference obsolete specifications — ISO updates standards regularly, and what was correct in 2010 may not match current requirements.

New XML-formatted specification files provide machine-readable symbol definitions. The Code 128 XML reference includes every character pattern with its numeric value, making it trivial to build encoders without manual transcription errors. Frankly, most barcode generator bugs I've seen stem from typos in lookup tables, and structured data eliminates that problem.

## New Barcode Standards and Specifications

ISO/IEC published updated editions of several critical standards in the past 18 months. ISO/IEC 16390:2023 (Interleaved 2 of 5) added formal guidance on bearer bars and quiet zone requirements that were previously "recommended practices" rather than mandatory specifications. If you're still using the 2007 edition for warehouse applications, check the dimensional tolerances — they've tightened.

The <a href="https://en.wikipedia.org/wiki/QR_code" rel="nofollow">QR Code</a> specification (ISO/IEC 18004) received a minor revision addressing error correction in Micro QR implementations. More interesting: the technical committee is working on extensions for encrypted data payloads. This isn't published yet, but draft proposals suggest native support for signing and verification within the symbology itself rather than at the application layer.

GS1's Digital Link standard has moved from pilot to production status. Instead of encoding just a GTIN in a barcode, Digital Link embeds a complete URL with product identifiers as path parameters. Scan a consumer product and the barcode resolves to a web page with nutrition data, recalls, authenticity verification — whatever the brand owner chooses to provide. The specification allows this in any 2D symbology, but DataMatrix is becoming the practical standard due to size constraints on product packaging.

According to GS1 data, Digital Link adoption is running about 18 months behind initial projections. The technology works fine; the holdup is backend infrastructure. Brands need web servers that respond to billions of product scans, and most companies aren't set up for that traffic pattern yet.

## Recent Additions to Resources

The [barcode FAQ section](/faq.html) has been completely rewritten. Previous version was written in 1998 and referenced outdated scanning hardware and operating systems. New version addresses modern implementation questions: camera-based scanning on mobile devices, symbology selection for inventory management, and integration with cloud-based systems.

New downloadable resources include updated font packages with proper licensing documentation. The free Code 39 fonts now include both TrueType and OpenType formats, tested on Windows 11, macOS Sonoma, and recent Linux distributions. Each download includes a specimen sheet showing proper quiet zones and a basic encoding guide.

Programming examples have been added for Python, JavaScript, and Go. The original site had C and Perl examples that still work but don't match how developers build applications in 2024. New code samples demonstrate integration with common frameworks — FastAPI, React, and standard library implementations that require no external dependencies.

## Industry News and Developments

The retail barcode transition is the biggest industry shift since the move from UPC to EAN in the 1980s. By January 2027, point-of-sale systems must scan 2D barcodes. This isn't optional — GS1 member companies (which includes essentially every major retailer and CPG brand) have committed to the timeline. Small retailers are scrambling because it means hardware upgrades: traditional laser scanners can't read DataMatrix codes.

Industry data shows only 23% of North American retailers have installed 2D-capable scanners at all checkout positions. The compliance deadline isn't moving, so expect a scramble in late 2026 when procurement teams realize they're out of time.

Healthcare has seen rapid adoption of GS1 DataBar for pharmaceutical track-and-trace. The Drug Supply Chain Security Act requires serialization at the unit level, and linear barcodes don't have sufficient data capacity. DataBar Expanded can encode a GTIN, serial number, lot, and expiration date in under 20mm width — critical for small-volume vials and ampules.

Manufacturing logistics is slowly shifting from Code 128 to QR codes for work-in-process tracking. The driver isn't data capacity (Code 128 handles most manufacturing data just fine) but omnidirectional scanning. Workers with ring scanners or phone-based apps can capture a QR code regardless of orientation. This reduces scan time in assembly operations where parts arrive in random orientations.

## Site Changelog and Announcements

Most recent technical update: correction to the Interleaved 2 of 5 specification page regarding check digit calculation. Previous version showed the modulo-10 algorithm but incorrectly stated it was optional for all implementations. ISO/IEC 16390 actually requires check digits for variable-length applications. Fixed the specification page and added a calculator tool.

Added historical context to the barcode history page covering the period between the 1952 patent and commercial deployment in 1974. That 22-year gap included failed implementations, competing technologies, and the development of laser scanning hardware. Understanding why early attempts failed provides useful context for evaluating new barcode technologies today.

Coming soon: dedicated section on camera-based scanning performance. Mobile device cameras now rival dedicated scanners for many applications, but optimal symbology selection differs from traditional laser scanning scenarios. Draft specifications are written; should publish next quarter.

The 2D barcode specifications page will be split into separate pages for each major symbology. Current single-page format is unwieldy for mobile users, and search engines prefer focused topic pages over lengthy guides. Content remains the same, just reorganized for better accessibility.

## Frequently Asked Questions

**Q: Are the barcode specifications on this site current with latest ISO standards?**

Yes for core symbologies, with a caveat. Pages like Code 128, Code 39, and Interleaved 2 of 5 reflect current published standards. Application-specific standards (like GS1-128 or healthcare barcodes) reference the latest versions but may lag a few months on minor revisions. When in doubt, the ISO/IEC standard itself is always the authoritative source — we provide implementation guidance, not the legal specification text.

**Q: Will the 2027 retail barcode transition affect my business?**

If you sell products through major retail channels, absolutely. Packaging printed after 2027 should include both traditional UPC and a GS1 DataMatrix code during the transition period. If you manufacture scanning equipment or point-of-sale software, your products must support 2D symbologies. For B2B operations outside retail, the transition has no direct impact, but it's accelerating adoption of 2D codes across all industries.

**Q: Why are some specification pages marked as legacy content?**

Several symbologies are technically obsolete but still appear in existing systems. Plessey code and Codabar are examples — no new implementations should use them, but warehouse systems from the 1990s still exist. Legacy pages remain available for maintenance work on old systems, but they're clearly marked to discourage use in new projects. When ISO withdraws a standard or GS1 deprecates a format, we move it to legacy status.