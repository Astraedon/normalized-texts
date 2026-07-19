# **King James Bible — Normalized Text Edition**

This repository contains a machine‑friendly, structurally tagged, punctuation‑normalized edition of the public‑domain King James Version (KJV). It includes both the **original Project Gutenberg text** and a fully **normalized version** prepared for research, tokenization, compression experiments, and structured text analysis.

---

## **Files Included**

### **`original.txt`**
The unmodified public‑domain KJV text from Project Gutenberg.

### **`normalized.txt`**
A fully normalized, structurally annotated version of the same text, produced using a deterministic preprocessing pipeline.

---

## **Source Attribution**

This work is derived from the **public domain** King James Bible provided by Project Gutenberg.

- Original source: [https://www.gutenberg.org/ebooks/10](https://www.gutenberg.org/ebooks/10)  
- License: Public Domain  
- No copyrighted material was used.

---

## **Normalization Pipeline**

The normalized text applies a consistent, reproducible transformation process designed to make the KJV suitable for machine processing while preserving all original wording.

### **1. Whitespace Normalization**
- Double spaces → single spaces  
- Double CRLF → single CRLF  
- No leading/trailing spaces  
- Exactly one CRLF between metadata and verse text  

### **2. Line Unwrapping**
Gutenberg wraps long verses across multiple lines. These were restored to single continuous lines using:

```
\r\n([^0-9]) → " $1"
```

### **3. Structural Metadata Insertion**
Each book, chapter, and verse is explicitly tagged:

```
{BOOK:Genesis}
{CHAPTER:1}
{VERSE:1}
```

### **4. Verse Marker Replacement**
Chapter/verse markers were detected and replaced using:

```
\b(\d+):1\b        → {CHAPTER:$1}\r\n{VERSE:1}\r\n
\b\d+:(\d+)\b      → {VERSE:$1}\r\n
```

### **5. Punctuation Normalization**
- punctuation spaced (`word , word . word :`)  
- no punctuation removed  
- temporary `BOOK~` substitution prevented colon collisions  

### **6. No Textual Alteration**
- no wording changes  
- no verse additions/removals  
- no spelling modernization  

---

## **Validation Counts**

The normalized text contains the correct canonical structure:

- **66** `{BOOK:` markers  
- **1189** `{CHAPTER:` markers  
- **31102** `{VERSE:` markers  

These counts match the standard KJV totals exactly.

---

## **Metadata Format**

Each structural unit is represented as:

```
{BOOK:Name}
{CHAPTER:n}
{VERSE:n}
Verse text...
```

---

## **License**

The text in this repository is derived from public‑domain sources and remains **public domain**.

Any code added later may be released under the **MIT License**.

---

## **Future Plans**

- Add per‑book normalized files  
- Add metadata files (books.json, verse index)  
- Add documentation of the full pipeline  
- Add parsing utilities  
- Add additional normalized public‑domain texts  
