# UBF Context Module

**Universal Binary Format - Context Module**  
**Version 1.0**  
Working Draft (2015-12-10)

**Dependencies**

- [`Module.Base`](./Module.Base.md)

## Grammar

### Production Rules

```ebnf
UBF =                                        (* UBF ----------------------- ! *)
  ...
  { Value                                    (* Value *)
  | Entry                                    (* Entry *)
  }
;
```
