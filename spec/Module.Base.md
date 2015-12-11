# UBF Base Module

**Universal Binary Format - Base Module**  
**Version 1.0**  
Working Draft (2015-12-10)

## Data Format

### Value Types

#### Dict

- `"\x10"` `uint8` = number of bytes `{ Entry }`
- `"\x11"` `uint16` `{ Entry }`
- `"\x12"` `uint32` `{ Entry }`

`Entry` ... `Key` `Value`

**Key**

- `"\xE0"` `uint8` = number of bytes `{ byte }`
- `"\xE1"` `uint16` `{ byte }`

`{ byte }` ... UTF-8 encoded characters

#### List

- `"\x14"` `uint8` = number of bytes `{ Value }`
- `"\x15"` `uint16` `{ Value }`
- `"\x16"` `uint32` `{ Value }`

#### String

- `"\x20"` `uint8` = number of bytes `{ byte }`
- `"\x21"` `uint16` `{ byte }`
- `"\x22"` `uint32` `{ byte }`

`{ byte }` ... UTF-8 encoded characters

#### Binary

- `"\x24"` `uint8` = number of bytes `{ byte }`
- `"\x25"` `uint16` `{ byte }`
- `"\x26"` `uint32` `{ byte }`

`{ byte }` ... binary data

#### Number

- `"\x30"` `int8` = Int8
- `"\x31"` `int16` = Int16
- `"\x32"` `int32` = Int32
- `"\x33"` `int64` = Int64
- `"\x38"` `float` = Float
- `"\x39"` `double` = Double

#### Boolean

- `"\x40"` = False
- `"\x41"` = True

#### Null

- `"\x42"` = Null

## Markers

**Reserved for Detecting [JSON](http://www.json.org/)**

- `\x5B` = `[` ... Array
- `\x7B` = `{` ... Object

## Grammar

### Terminal Symbols

```ebnf
byte   = (* 1 byte *);

uint8  = (* 1 byte ;  8-bit unsigned integer *);
uint16 = (* 2 bytes; 16-bit unsigned integer *);
uint32 = (* 4 bytes; 32-bit unsigned integer *);

int8   = (* 1 byte ;  8-bit signed integer, two's complement *);
int16  = (* 2 bytes; 16-bit signed integer, two's complement *);
int32  = (* 4 bytes; 32-bit signed integer, two's complement *);
int64  = (* 8 bytes; 64-bit signed integer, two's complement *);

float  = (* 4 bytes; 32-bit IEEE 754 floating point *);
double = (* 8 bytes; 64-bit IEEE 754 floating point *);
```

Byte order: [`big-endian`](https://en.wikipedia.org/wiki/Endianness#Big-endian)

### Production Rules

```ebnf
UBF =                                        (* UBF ----------------------- ! *)
  ["\xFF" "\x23" "\x42" "\x00"]              (* Magic Number (optional) *)
  { Value }                                  (* Value *)
;

Value =                                      (* Value ----------------------- *)
    BaseValue                                (* Value (Base) *)
;

BaseValue =                                  (* Value ------------------ Base *)
    BaseValueDict                            (* Dict *)
  | BaseValueList                            (* List *)

  | BaseValueString                          (* String *)
  | BaseValueBinary                          (* Binary *)

  | BaseValueNumber                          (* Number *)
  | BaseValueBoolean                         (* Boolean *)
  | BaseValueNull                            (* Null *)
;

BaseValueDict =                              (* Dict ------------------- Base *)
    "\x10" uint8  { Entry }                  (* max 254 bytes *)
  | "\x11" uint16 { Entry }                  (* max 65,534 bytes *)
  | "\x12" uint32 { Entry }                  (* max 2,147,483,647 bytes *)
;

BaseValueList =                              (* List ------------------- Base *)
    "\x14" uint8  { Value }                  (* max 254 bytes *)
  | "\x15" uint16 { Value }                  (* max 65,534 bytes *)
  | "\x16" uint32 { Value }                  (* max 2,147,483,647 bytes *)
;

BaseValueString =                            (* String ----------------- Base *)
    "\x20" uint8  { byte }                   (* max 254 bytes *)
  | "\x21" uint16 { byte }                   (* max 65,534 bytes *)
  | "\x22" uint32 { byte }                   (* max 2,147,483,647 bytes *)
;

BaseValueBinary =                            (* Binary ----------------- Base *)
    "\x24" uint8  { byte }                   (* max 254 bytes *)
  | "\x25" uint16 { byte }                   (* max 65,534 bytes *)
  | "\x26" uint32 { byte }                   (* max 2,147,483,647 bytes *)
;

BaseValueNumber =                            (* Number ----------------- Base *)
    "\x30" int8                              (* Int8 *)
  | "\x31" int16                             (* Int16 *)
  | "\x32" int32                             (* Int32 *)
  | "\x33" int64                             (* Int64 *)
  | "\x38" float                             (* Float *)
  | "\x39" double                            (* Double *)
;

BaseValueBoolean =                           (* Boolean ---------------- Base *)
    "\x40"                                   (* False *)
  | "\x41"                                   (* True *)
;

BaseValueNull =                              (* Null ------------------- Base *)
    "\x42"                                   (* Null *)
;

Entry =                                      (* Entry ----------------------- *)
    Key Value
;

Key =                                        (* Key ------------------------- *)
    BaseKey                                  (* Key (Base) *)
;

BaseKey =                                    (* Key -------------------- Base *)
    "\xE0" uint8  { byte }                   (* max 254 bytes *)
  | "\xE1" uint16 { byte }                   (* max 65,534 bytes *)
;
```
