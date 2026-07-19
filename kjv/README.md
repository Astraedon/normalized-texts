# **Normalized KJV Text Dataset**

A machine‑interpretable, structurally tagged edition of the public‑domain King James Version of the Bible. Includes the original Project Gutenberg text and a normalized version suitable for parsing, tokenization, and text‑analysis research.

---

## **Source**

**Project Gutenberg eBook of The King James Version of the Bible**  
[https://www.gutenberg.org/ebooks/10](https://www.gutenberg.org/ebooks/10)  
Public Domain

---

## **Files**

- **original.txt** — downloaded directly from the Project Gutenberg source  
- **normalized.txt** — normalized using the rules listed below  
- **tokens.txt** — complete list of distinct tokens (generated from normalized text)

---

## **Normalization Rules**

- Removed Gutenberg introduction and summary  
- Replaced book boundaries with `{BOOK:Name}` tags  
- Detected chapter/verse headers using regex:  
  ```
  \b(\d+:\d+)\b
  ```
- Replaced chapter boundaries with `{CHAPTER:Number}` tags  
- Replaced verse boundaries with `{VERSE:Number}` tags  
- Unwrapped verses by replacing line endings not preceding metadata with spaces  
- Removed all hyphens (per previous research)  
- Separated punctuation into standalone tokens:  
  `, ; : ! ? . ( )`  
- Replaced multiple CRLFs with a single CRLF  
- Replaced multiple spaces with a single space  
- Trimmed leading/trailing whitespace on all lines  

---

## **Structural Counts (Verified)**

- **BOOK:** 66  
- **CHAPTER:** 1189  
- **VERSE:** 31102  
