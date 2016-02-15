# ![UBF][ubf-img]

[ubf-img]: http://static.ubfspec.org/img/ubf.svg

**Universal Binary Format (UBF) - Context**  
**Version 1.0**  
Working Draft (2016-02-10)

#### Dependencies
- [`Base`](./Base.md)

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
