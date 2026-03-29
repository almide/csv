# almide/csv

CSV parser and serializer for [Almide](https://github.com/almide/almide). Pure Almide implementation with RFC 4180 support.

## Install

```bash
almide add csv
```

## Usage

```almide
import csv

// Parse CSV text to array of arrays
let data = csv.parse("name,age\nAlice,30\nBob,25")!

// Parse with header row → array of objects
let records = csv.parse_records("name,age\nAlice,30\nBob,25")!

// Stringify array of arrays
let text = csv.stringify(data)

// Stringify array of objects (auto-generates header)
let text = csv.stringify_records(records)
```

## API

| Function | Signature | Description |
|---|---|---|
| `csv.parse` | `(String) -> Result[Value, String]` | Parse to array of arrays |
| `csv.parse_records` | `(String) -> Result[Value, String]` | Parse with header row → array of objects |
| `csv.stringify` | `(Value) -> String` | Serialize array of arrays to CSV |
| `csv.stringify_records` | `(Value) -> String` | Serialize array of objects to CSV (with header) |

## Features

- Quoted fields (`"hello, world"`)
- Escaped quotes (`""` → `"`)
- Newlines within quoted fields
- CRLF and LF line endings
- Empty fields
- Roundtrip-safe: parse then stringify preserves data

## License

MIT
