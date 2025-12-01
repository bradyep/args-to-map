# args-to-map

## Purpose

Simple utility to convert command line arguments to a Map object in a node process.

## Installation

```bash
npm install args-to-map
```

## Usage

### Basic Usage

By default, all arguments are treated as strings. Flags (starting with `--` or `-`) without a value default to `"true"`.

```typescript
import { ArgsToMap } from "args-to-map";

// Assume command: node script.js --name "John Doe" --verbose
const args = process.argv.slice(2);
const argsMap = ArgsToMap.getArgsAsMap(args);

console.log(argsMap.get("name")); // "John Doe"
console.log(argsMap.get("verbose")); // "true"
```

### Aliases

You can map single-character aliases (like `-v`) to full option names (like `verbose`).

```typescript
import { ArgsToMap } from "args-to-map";

// Assume command: node script.js -n "Jane" -v
const args = process.argv.slice(2);
const aliases = {
  n: "name",
  v: "verbose"
};

const argsMap = ArgsToMap.getArgsAsMap(args, aliases);

console.log(argsMap.get("name")); // "Jane"
console.log(argsMap.get("verbose")); // "true"
```

### Type Conversion

If you pass `true` as the third argument, the utility will attempt to convert values to `boolean` or `number`.

```typescript
import { ArgsToMap } from "args-to-map";

// Assume command: node script.js --count 42 --isActive true --mode "fast"
const args = process.argv.slice(2);
const aliases = {};
const attemptTypeConversion = true;

const argsMap = ArgsToMap.getArgsAsMap(args, aliases, attemptTypeConversion);

console.log(argsMap.get("count")); // 42 (number)
console.log(argsMap.get("isActive")); // true (boolean)
console.log(argsMap.get("mode")); // "fast" (string)
```

## Misc Notes

TypeScript's type system has limitations with string literal length checks in object keys, so perfect compile-time validation is challenging.

## License

MIT
