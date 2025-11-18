# WAFL Language Support

Syntax highlighting and editor helpers for WAFL (`.wafl`) configuration files.

## Features

- **Syntax highlighting** for directives, type annotations, inline expressions, and tag calls
- **Auto-closing** of brackets/quotes and `#` line comments
- **Indent-based folding** for nested blocks and lists

## Language coverage

- **Directives**: `@import`, `@schema`, `@eval`
- **Type annotations**: `key<Type>` markers on objects/fields
- **Inline expressions**: `key = <js expression>` with `$ENV.*` access
- **Conditional items**: `- if <expr>: <value>` inside lists
- **Tags**: `!tag(...)` calls, including built-ins `!rgb(r,g,b)` and `!file(path)`

## Installation

### From Marketplace

Search for _“WAFL Language Support”_ in the VS Code Marketplace.

## Usage

The extension activates automatically for `.wafl` files.

## Example

```
@schema:
  App:
    name: string
    version: string
    port: int
    debug?: bool
    theme:
      primary: string
      secondary: string
    features: list<string>

app<App>:
  name: "WAFL Demo"
  version: "1.0.0"
  port = $ENV.PORT || 3000
  debug = $ENV.NODE_ENV === "dev"

  theme:
    primary = !rgb(255, 200, 80)
    secondary = "#111"

  features:
    - login
    - analytics
    - if $ENV.NODE_ENV === "dev": monitoring
```
