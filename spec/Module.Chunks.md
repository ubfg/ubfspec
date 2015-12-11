# UBF Chunks Module

**Universal Binary Format - Chunks Module**  
**Version 1.0**  
Working Draft (2015-12-10)

**Dependencies**

- [`Module.Base`](./Module.Base.md)

## Grammar

### Production Rules

```ebnf
Value =                                      (* Value ----------------------- *)
    ...
  | ChunksValue                              (* Value (Chunks) *)
;

ChunksValue =                                (* Value ---------------- Chunks *)
    "\x1C" { Entry }           "\x00"        (* Dict *)
  | "\x1D" { Value }           "\x00"        (* List *)

  | "\x2C" { BaseValueString } "\x00"        (* String *)
  | "\x2D" { BaseValueBinary } "\x00"        (* Binary *)
;
```
