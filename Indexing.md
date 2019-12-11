# Bigger Than Memory

- CSV
- XML
- JSON
- Multipart

# Streaming vs Random Access

- Secuential Forward Only
- Random Access

# Parser

- In memory dom
- In disk storage

# In Disk

- Indexed Parser 

# Tokenization

Split Into Keywords a Document

# Navigation

Randomly navigate to any child element

# Token Table

Two Long Array  per token

# Token Table (Xml Key)

16 Byte

- Starting offset : 52 bits
- Nesting depth: 12 bits
- Token type: 4 bits
- Hash: 16 bits
- Namespace index: 12 bits
- Qname length: 32 bits

# Location Cache

One Array<Long> Per Depth

# Location Cache

8 Bytes

- Pointer To Token Table: 4 Bytes
- Pointer To First Child On Next Depth: 4 Bytes


# Links

- https://en.wikipedia.org/wiki/VTD-XML
- https://www.infoq.com/articles/HIgh-Performance-Parsers-in-Java-V2/