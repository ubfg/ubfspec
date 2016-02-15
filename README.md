# ![UBF][ubf-img]

[ubf-img]: http://static.ubfspec.org/img/ubf.svg

**Universal Binary Format (UBF)**  
A Modular Binary Format For Data Interchange

## Description
_TODO_

## Modules

### Base
See [`Base`](./modules/Base.md)

### Context
See [`Context`](./modules/Context.md)

### Chunks
See [`Chunks`](./modules/Chunks.md)

### Constant Pool
See [`ConstantPool`](./modules/ConstantPool.md)

### Custom Types
_TODO_

### Metadata
_TODO_

### Structs
_TODO_

## Information

##### Type of Format
`Data Interchange`

##### Media Type
`application/ubf`

##### File Extension
`*.ubf`

##### Endianness
[`big-endian`](https://en.wikipedia.org/wiki/Endianness#Big-endian)

## Implementations

#### JavaScript (ECMAScript)

##### [js-ubf](https://github.com/ubfg/js-ubf)
_Current Reference Implementation_

- **Parser**  
  `Base`, `Context`, `Chunks`, `ConstantPool`
- **Binarifier**  
  `Base`
