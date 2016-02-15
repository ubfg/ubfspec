# ![UBF][ubf-img]

[ubf-img]: http://static.ubfspec.org/img/ubf.svg

**Universal Binary Format (UBF) - Constant Pool**  
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
  | ConstantPoolValue                        (* Value (Constant Pool) *)
;

ConstantPoolValue =                          (* Value --------- Constant Pool *)
    "\xC0" uint8                             (* read; maxID 254 *)
  | "\xC1" uint16                            (* read; maxID 65,534 *)

  | "\xC2" uint8  Value(-ConstantPoolValue)  (* write; maxID 254 *)
  | "\xC3" uint16 Value(-ConstantPoolValue)  (* write; maxID 65,534 *)
;

Key =                                        (* Key ------------------------- *)
    ...
  | ConstantPoolKey                          (* Key (Constant Pool) *)
;

ConstantPoolKey =                            (* Key ----------- Constant Pool *)
    "\xC4" uint8                             (* read; maxID 254 *)
  | "\xC5" uint16                            (* read; maxID 65,534 *)

  | "\xC6" uint8  Key(-ConstantPoolKey)      (* write; maxID 254 *)
  | "\xC7" uint16 Key(-ConstantPoolKey)      (* write; maxID 65,534 *)
;
```
