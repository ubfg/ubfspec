# UBF Constant Pool Module

**Universal Binary Format - Constant Pool Module**  
**Version 1.0**  
Working Draft (2015-12-10)

**Dependencies**

- [`Module.Base`](./Module.Base.md)

## Grammar

### Production Rules

```ebnf
ValueNoConstantPool =                        (* Value ------ No Constant Pool *)
    Value
;

Value =                                      (* Value ----------------------- *)
    ValueNoConstantPool
  | ConstantPoolValue                        (* Value (Constant Pool) *)
;

ConstantPoolValue =                          (* Value --------- Constant Pool *)
    "\xC0" uint8                             (* read; maxID 254 *)
  | "\xC1" uint16                            (* read; maxID 65,534 *)

  | "\xC2" uint8  ValueNoConstantPool        (* write; maxID 254 *)
  | "\xC3" uint16 ValueNoConstantPool        (* write; maxID 65,534 *)
;

KeyNoConstantPool =                          (* Key -------- No Constant Pool *)
    Key
;

Key =                                        (* Key ------------------------- *)
    KeyNoConstantPool
  | ConstantPoolKey                          (* Key (Constant Pool) *)
;

ConstantPoolKey =                            (* Key ----------- Constant Pool *)
    "\xC4" uint8                             (* read; maxID 254 *)
  | "\xC5" uint16                            (* read; maxID 65,534 *)

  | "\xC6" uint8  KeyNoConstantPool          (* write; maxID 254 *)
  | "\xC7" uint16 KeyNoConstantPool          (* write; maxID 65,534 *)
;
```
