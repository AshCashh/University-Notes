---
tags: [cs]
Created: 2024-03-01T20:24:12+10:00
Modified: 2024-07-03T19:27:34+10:00
---
Unicode, formally The Unicode Standard is a text [[Encoding]] standard maintained by the Unicode Consortium designed to support the use of text written in all of the world's major writing systems including [[Computer System|Computers]]. Version 15.1 of the standard defines 149,813 characters and 161 scripts used in various ordinary, literary, academic and technical contexts.

Many common characters including numerals, punctuation and other symbols are unified within the standard and are not treated as specific to any given writing system. Unicode encodes thousands of emoji's along with mathematical symbols.

Unicode assigns a code point (a [[Hexadecimal]] string) for each character. There are several different encodings from code points to [[Binary|bit]] strings.
- UTF32 uses 32 bits for each character, encoding code points directly
- UTF16 uses one or two 16-bit strings per code points, making it a variable length encoding
- UTF8 is the most common encoding and uses between one and four 8-bit strings per code point, and is hence also a variable length encoding. It is backwards and compatible with [[ASCII]] for the original 7-bit ASCII character set.