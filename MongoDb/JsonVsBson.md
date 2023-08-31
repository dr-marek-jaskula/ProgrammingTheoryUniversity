# Json vs Bson

JSON and BSON are indeed close cousins by design. BSON is designed as a binary representation of JSON data, with specific extensions for broader applications, and optimized for data storage and traversal. Just like JSON, BSON supports embedding objects and arrays. 

Json is:

- Encoded: UTF-8 string 
- Data Support: String, Boolean, Number, Array, Object, null
- Readability: Human and Machine

Bson is:

- Encoded: Binary
- Data Supported: String, Boolean, Number (Integer, Float, Long, Decimal128...), Array, null, Date, BinData
- Readability: Machine Only

ObjectId is a BSON type.

## Json and Bson 

Json -> Bson

```
{"hello": "world"} →
\x16\x00\x00\x00           // total document size
\x02                       // 0x02 = type String
hello\x00                  // field name
\x06\x00\x00\x00world\x00  // field value
\x00                       // 0x00 = type EOO ('end of object')
```

```
{"BSON": ["awesome", 5.05, 1986]} →
\x31\x00\x00\x00
 \x04BSON\x00
 \x26\x00\x00\x00
 \x02\x30\x00\x08\x00\x00\x00awesome\x00
 \x01\x31\x00\x33\x33\x33\x33\x33\x33\x14\x40
 \x10\x32\x00\xc2\x07\x00\x00
 \x00
 \x00
```