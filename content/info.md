---
title: "BarCode-1 Site Contents Page - Navigation & Resources"
description: "Navigate BarCode-1's complete technical documentation including Code 39, Code 128, UPC/EAN specifications, free barcode fonts, developer tools, and the original"
url: "/info.html"
date: 2026-07-13
weight: 954
image: "/images/info.jpg"
---

This site contents page maps BarCode-1's technical documentation, software tools, and barcode standards resources. Direct links to specifications, downloads, historical documents including the original 1952 barcode patent, and implementation guides organized by symbology type.

## Complete Site Map and Navigation

BarCode-1 organizes content into categories matching actual barcode workflow: symbology selection, application requirements, and implementation steps. The main navigation begins with [fundamental barcode resources](/pub) covering encoding principles before addressing specific standards.

Linear symbologies form the technical core: [Code 39](/39code.html) for alphanumeric applications, [Code 128](/128code.html) for high-density variable-length data, and [Interleaved 2 of 5](/i25code.html) for numeric-only warehouse systems. Each symbology page includes character tables, encoding rules per ISO/IEC specifications, and implementation examples. Code 39 remains popular despite 30% lower density than Code 128 because it requires simpler decode logic.

The [UPC and EAN guide](/upccode.html) covers retail barcodes with conversion utilities and check digit calculators. For supply chain applications, the [UCC/EAN-128 page](/ucc128.html) details Application Identifier structures according to <a href="https://www.gs1.org/" rel="nofollow">GS1 standards</a>. Two-dimensional codes receive dedicated coverage on the [2D barcode page](/stack.html), including PDF417, Data Matrix, and QR Code specifications.

The [barcode history section](/history.html) traces development from Woodland and Silver's 1952 patent through modern implementations. That original patent document is available as a [downloadable PDF](/shareware/2612994.pdf) — worth reading to see how circular bulls-eye patterns preceded the now-universal linear format.

## Available Resources and Tools

The software sections provide immediate utility for developers working across multiple platforms.

The [barcode fonts page](/fonts.html) offers free downloads including Code 3 of 9 TrueType fonts and USPS Postnet fonts. These are production-ready tools for printing barcodes directly from standard applications. The [Interleaved 2 of 5 font](/shareware/i2of5txt.zip) generates proper start/stop patterns and includes mandatory check digit calculation — critical since I-2/5 lacks self-checking like Code 128.

For Unix and Linux environments, the [Unix barcode programs page](/unix.html) catalogs command-line tools and library implementations. These integrate directly into warehouse management systems without Windows dependencies. Several Fortune 500 distribution centers run label generation entirely through these command-line tools.

Web-based tools live on the [barcode web software page](/webapps.html) — browser-based generators for quick prototyping and small-batch label production. No installation required.

Developer resources include [plugins and VBX controls](/plugins.html) for integrating barcode generation into custom applications. These libraries handle the encoding logic so developers focus on business rules rather than symbology mathematics.

## Documentation and Specifications

Standards documentation forms the backbone of interoperable barcode systems. The [specifications source page](/pub/russadam/spec.html) aggregates links to authoritative references including ISO/IEC standards documents and GS1 General Specifications.

Code 128 deserves attention given its dominance in logistics — approximately 80% of North American shipping labels use it. The [Code 128 character table](/128table.html) lists all 106 symbol patterns with corresponding values in Code Set A, B, and C. For programmatic access, structured [Code 128 XML data](/pub/russadam/128code.xml) provides machine-readable specifications.

Lesser-known symbologies serve niche applications. The [Plessey barcode page](/plessy.html) covers this UK retail standard, while historical patent documents like <a href="/patents/us4745269.pdf" rel="nofollow">US Patent 4,745,269</a> detail innovations in dot code technology.

The [FAQ section](/faq.html) answers recurring implementation questions about quiet zones, check digits, and scanner compatibility — issues that consistently trip up first-time implementers.

## Software Downloads and Links

The [shareware section](/share.html) consolidates free and trial software across Windows, Mac, and Linux platforms. Download links include version numbers and compatibility information.

Specific downloads: the [Code 3 of 9 font package](/shareware/3of9_new.zip) includes installation instructions and character mapping guide. The [USPS Postnet TrueType font](/shareware/uspsbarcode.ttf) generates postal barcodes compliant with USPS-B-3200 specifications for automated mail sorting.

Label printing software gets dedicated coverage on the [barcode label printing page](/label.html). These tools handle layout, batch printing, and database integration — essential for warehouses managing thousands of SKUs.

## Contact and Support Information

Technical questions and site feedback use the contact channels listed on individual resource pages. For specific symbology questions, the relevant specification page includes references to the governing standards body.

The [What's New page](/new.html) tracks recent additions, updated specifications, and new software releases. Check there first for latest GS1 Application Identifier additions or revised ISO standards.

For general barcode technology questions not covered in technical pages, the FAQ provides troubleshooting guidance.

## Frequently Asked Questions

**Q: How do I choose the right barcode symbology for my application?**

Start with your data type and length. UPC-A works for fixed 12-digit retail products. Code 128 handles variable-length alphanumeric data up to several dozen characters. Code 39 sacrifices density for simple implementation. Interleaved 2 of 5 is the most compact option for numeric-only data in pairs. Check the symbology-specific pages for detailed decision criteria including scanner compatibility and label size constraints.

**Q: Are the barcode fonts and software really free to use commercially?**

Most fonts marked as "free" permit commercial use, but verify the license file included with each download. Some shareware requires registration for commercial deployment. The Code 3 of 9 and USPS Postnet fonts explicitly permit commercial use without fees. When uncertain, check the readme file in the download package.

**Q: Where can I find the official ISO specifications for barcode standards?**

The specifications source page links to publicly available standards documents where permitted. Full ISO/IEC standards require purchase from ISO or national standards bodies. However, many implementation guides and symbology pages here provide sufficient technical detail for most development projects. GS1 specifications are freely available from GS1.org for UPC, EAN, and GS1-128 implementations.