# ![UBF][ubf-img]

[ubf-img]: http://static.ubfspec.org/img/ubf.svg

**Universal Binary Format (UBF) - Chunks**  
**Version 1.0**  
Working Draft (2016-02-10)

#### Dependencies
- [`Base`](./Base.md)
- [`Context`](./Context.md)

## Grammar

### Production Rules

```ebnf
Value =                                      (* Value ----------------------- *)
    ...
  | ChunksValue                              (* Value (Chunks) *)
;

ChunksValue =                                (* Value ---------------- Chunks *)
    "\x1C" { Entry }           "\x1F"        (* Dict *)
  | "\x1D" { Value }           "\x1F"        (* List *)

  | "\x2C" { BaseValueString } "\x2F"        (* String *)
  | "\x2D" { BaseValueBinary } "\x2F"        (* Binary *)
;
```
