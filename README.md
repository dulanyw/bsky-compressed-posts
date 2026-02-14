# Bluesky Unicode Compressor

Lossless text compression designed to squeeze large blocks of text into Bluesky's **300-grapheme post limit**. Wholly vibe-coded and AI-generated in early 2026, so set your quality expectations appropriately.

This tool compresses text using pako, then encodes the compressed bytes into a very large Unicode alphabet so that each output grapheme carries far more entropy than Base64 or Base85.

In short:

Text → UTF-8 → Compress → High-radix Unicode encoding → Post to Bluesky

------------------------------------------------------------------------

## Why This Exists

Bluesky limits posts to **300 graphemes**.

Traditional encodings (Base64, Base85) waste character space because
they only use small alphabets. This tool:

-   Uses real compression
-   Uses a huge Unicode alphabet (\~20k+ characters)
-   Ensures every output symbol is a single codepoint (no ZWJ sequences)
-   Verifies integrity with CRC32

Example:

975 graphemes → 274 graphemes\
Compression ratio ≈ 0.28 (3.56:1)

------------------------------------------------------------------------

## Usage

0.  Open the webpage.
1.  Paste plain text (English, URLs, etc.) into the "Text" box.
2.  Click Encode.
3.  Copy the encoded blob.
4.  Post it to Bluesky.
5.  To decode, paste the blob back into the "Blob" box and click Decode.

------------------------------------------------------------------------

## Compression Behavior

  Content Type      Expected Result
  ----------------- ---------------------------------
  Plain English     Excellent (often 3--5× smaller)
  Repetitive text   Very high compression
  URLs              Moderate
  Random data       Minimal compression

Natural language compresses very well.

------------------------------------------------------------------------

## Alphabet Strategy

The encoder uses:

-   ASCII letters + punctuation
-   Greek
-   Cyrillic
-   Hiragana
-   Katakana
-   Hangul syllables
-   CJK Unified Ideographs (\~20k characters)
-   Emoji (single-codepoint faces block)

All are single codepoints with no ZWJ sequences to maximize entropy per grapheme.

------------------------------------------------------------------------

## Notes

-   Bluesky counts graphemes, not bytes.
-   If any character is altered during copy/paste, CRC verification will fail.
-   Large blobs exceeding 300 graphemes will not fit in one post.

------------------------------------------------------------------------

## License

CC BY-SA. This is a silly but fun experiment - if you're able to improve on this (and there is a lot of room for improvement!), please ping me to share what you've done!
