# UBF Specification

**Universal Binary Format (UBF)**  
**Version 1.0**  
Working Draft (2015-12-10)

## Description

A modular binary format for data interchange.

## Profiles

### Base

See [Profile.Base](./spec/Profile.Base.md)

## Modules

### Base

See [Module.Base](./spec/Module.Base.md)

### Chunks

See [Module.Chunks](./spec/Module.Chunks.md)

### Constant Pool

See [Module.ConstantPool](./spec/Module.ConstantPool.md)

### Context

See [Module.Context](./spec/Module.Context.md)

### Custom Types

See Module.CustomTypes

### Metadata

See Module.Metadata

### Structs

See Module.Structs

## Information

**Type of Format**

`Data Interchange`

**Media Type**

`application/ubf`

**File Extension**

`*.ubf`

**Endianness**

[`big-endian`](https://en.wikipedia.org/wiki/Endianness#Big-endian)

## Notes

## Implementations

### JavaScript (ECMAScript)

**[js-ubf](https://github.com/ubfg/js-ubf)**  

| Component    | Implements |
|--------------|------------|
| `Parser`     | `Profile.Base` |
| `Binarifier` | `Profile.Base` |
