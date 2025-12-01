# args-to-map

## Purpose

Simple utility to convert command line arguments to a Map object in a node process.

## Usage

```ts
import { ArgsToMap } from "./args-to-map.js";

const argsMap: Map = ArgsToMap(process.argv);
```

### Aliases

### Type Conversion

## Misc Notes

TypeScript's type system has limitations with string literal length checks in object keys, so perfect compile-time validation is challenging.

## License

MIT
