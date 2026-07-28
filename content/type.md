---
title: "Type 3.2 - Professional Font Editor Software"
description: "Type 3.2 font editor from CR8 Software offers professional TrueType and OpenType editing with kerning, hinting, and OpenType features at £149-£199—one-quarter t"
url: "/type.html"
date: 2026-07-09
weight: 909
image: "/images/type.jpg"
---

Type 3.2 is a professional-grade TrueType and OpenType font editor from CR8 Software Solutions Ltd that bridges the gap between entry-level tools and expensive industry standards like FontLab. It offers precise Bézier curve manipulation, kerning tables, and hinting controls at a fraction of the cost, making it particularly useful for designers creating custom barcode fonts, symbol libraries, or modifying existing typefaces for corporate branding work.

## Introduction to Type 3.2 font editor by CR8 Software

CR8 Software Solutions developed Type 3.2 as their flagship font editing application, positioning it above their freeware offering [Type Light](/typelight.html) but without the price tags of FontLab Studio (currently $799) or Glyphs (€299). The software targets working designers who need proper OpenType feature support and GSUB table editing but don't require the variable font authoring or multi-master capabilities that professional type foundries demand.

Type 3.2 reads and writes standard TTF and OTF formats with full Unicode support up to version 13.0. I've used it extensively for modifying GS1 DataBar fonts where precise vector control matters—those narrow bar widths demand sub-pixel accuracy that you simply can't achieve in Illustrator's glyph panel. The software handles composite glyphs properly, which is essential when building accented characters or creating modular symbol sets.

Unlike its free sibling, Type 3.2 includes professional hinting tools (both TrueType and PostScript), a complete kerning editor with class-based pair management, and OpenType feature compilation directly in the interface. You're not exporting to AFDKO command-line tools or maintaining separate .fea files—everything compiles within the application.

## Advanced font design and editing features

The core glyph editor in Type 3.2 uses a dual-layer drawing system: off-curve Bézier handles appear in green, on-curve points in black. Right-click context menus toggle point types (corner, curve, tangent) without keyboard memorization. This matters when you're adjusting barcode quiet zones at 11pm before a print deadline—clarity beats cleverness.

The program supports both quadratic (TrueType) and cubic (PostScript) curve mathematics. When importing EPS outlines from Illustrator, Type 3.2 converts cubic curves to quadratic approximations with adjustable error thresholds. Set it to 0.5 units for precise work; bump it to 2.0 units for faster conversions when exactness matters less. I typically keep it at 1.0—good enough for text faces, tight enough for technical symbols.

Hinting controls live in a separate panel with visual preview at multiple point sizes. You can add stem hints, ghost hints, and alignment zones without touching raw TT instructions. The auto-hinter produces decent results for Latin alphabets but needs manual adjustment for custom barcode fonts where vertical alignment across glyphs is critical. For related vector work, check out [CR8tracer](/tracer.html) for converting scanned logos into editable outlines.

The kerning editor displays pair lists in spreadsheet format with real-time preview. Create kerning classes (all rounded characters, all straight stems) and apply adjustments globally. This workflow beats manually kerning 4,000 individual pairs when building a complete commercial typeface. Type 3.2 imports AFM kerning data from legacy PostScript fonts, useful when modernizing older corporate identity fonts to OpenType.

## Professional typography tools and capabilities

OpenType feature support in Type 3.2 covers the essentials: ligatures (liga, dlig), contextual alternates (calt), stylistic sets (ss01-ss20), small caps (smcp), oldstyle figures (onum), and fractions (frac). You write feature code in Adobe's .fea syntax—the software includes a basic validator that catches bracket mismatches and missing lookups before compilation.

Honestly, the feature editor isn't as polished as FontLab's visual interface or Glyphs' automatic feature generation. You're writing code. But for barcode fonts or symbol libraries where you need specific substitution rules (swapping module widths based on surrounding characters), direct feature access proves more flexible than GUI abstractions.

The software includes metric management for setting font-wide parameters: units per em (typically 1000 for OTF, 2048 for TTF), cap height, x-height, ascender, descender values. These numbers matter when your custom barcode font needs to align with Helvetica in a label template—matching x-heights means mixed text flows naturally without manual baseline adjustments.

Type 3.2 generates proper <a href="https://en.wikipedia.org/wiki/OpenType" rel="nofollow">OpenType</a> name tables with manufacturer, designer, copyright, and licensing fields. Fill these out properly; professional print shops and brand management teams actually check this metadata when auditing font licenses.

One limitation: no variable font authoring. If you need multiple-master interpolation or axes (weight, width, optical size), you'll need FontLab 8 or Glyphs 3. Type 3.2 focuses on static font instances—one file, one style.

## Pricing and licensing information

CR8 Software sells Type 3.2 as commercial software with perpetual licensing. Pricing sits around £149-£199 depending on regional currency. That's roughly one-quarter the cost of FontLab Studio, making it viable for freelance designers who bill font modification as project work rather than daily production.

The license permits installation on two machines (typically desktop + laptop) per user. No subscription model, no cloud requirements, no phone-home DRM beyond initial activation. You own the software version you purchase; major upgrades (like jumping from v3 to hypothetical v4) typically require upgrade fees.

Educational discounts exist for students and faculty—approximately 40% off standard pricing with valid .edu email verification. Worth investigating if you're teaching type design courses without departmental budgets for FontLab site licenses.

For detailed techniques that apply across Type 3.2 and similar tools, read our guide on <a href="https://fontforge.org/docs/tutorial/bezier.html" rel="nofollow">Bézier curve fundamentals</a>.

## Platform compatibility and download options

Type 3.2 runs exclusively on Windows—Windows 10 and 11 confirmed, Windows 7 support ended with version 3.1. No macOS version exists despite requests on typography forums. CR8 Software maintains a Windows-first development approach across their entire product line.

Minimum system requirements are modest: 2GB RAM, 200MB disk space, 1280×800 display resolution. The software isn't GPU-accelerated; all rendering happens via GDI+ on the CPU. Works fine on budget laptops, though complex glyphs with hundreds of points can lag slightly during curve manipulation on older Core i3 processors.

Download Type 3.2 directly from CR8 Software's website as a ~25MB installer (type3setup.exe). The trial version runs fully functional for 30 days with no feature restrictions—rare in font software where trials often disable export or add watermarks. Use those 30 days to test OpenType feature compilation with your actual fonts, not toy specimens.

Installation requires administrator rights for proper TrueType rasterizer integration with Windows. The software installs TrueType instruction debuggers that hook into the system font cache—standard practice for professional font editors but flagged by overzealous antivirus software occasionally.

Updates arrive via manual download rather than auto-updaters. Check the CR8 Software site quarterly for point releases (3.2.1, 3.2.2) that fix Unicode mapping bugs or add glyphs for new emoji blocks.

## Frequently Asked Questions

**Q: Can Type 3.2 edit variable fonts or create multiple-master interpolations?**

No. Type 3.2 focuses on static font instances—single-style TTF or OTF files. Variable font authoring requires dedicated axis management, delta-set indexing, and multi-master interpolation that Type 3.2 doesn't provide. For variable font work, you need FontLab 8, Glyphs 3, or the open-source FontForge. However, Type 3.2 excels at editing individual instances extracted from variable fonts when you need to modify a specific weight without rebuilding the entire family.

**Q: How does Type 3.2 compare to the free Type Light version for barcode font development?**

Type Light handles basic glyph editing and TTF export but lacks kerning tables, OpenType features, and hinting controls. For simple barcode fonts where each character stands alone (Code 39, Code 128), Type Light suffices. But if you're building composite barcodes with check digits, human-readable text zones, or GS1 DataBar variants requiring contextual substitutions, Type 3.2's OpenType feature compiler becomes essential. The professional version also includes batch glyph operations and scriptable actions that save hours when building 256-character symbol sets.

**Q: Does Type 3.2 support importing SVG color fonts or bitmap emoji?**

Partially. Type 3.2 imports monochrome SVG outlines and converts them to standard vector paths, useful for incorporating icon designs from Illustrator. However, it doesn't support COLR/CPAL layered color tables or SBIX/CBDT bitmap emoji formats introduced in newer OpenType specifications. For color font creation, look at FontLab 8 or the specialized Fontself extension for Adobe Creative Cloud applications. Type 3.2 remains focused on traditional outline fonts—which honestly covers 95% of professional typography work outside consumer messaging apps.