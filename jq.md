# jq Documentation: Introduction

## Why Use jq?

JSON (JavaScript Object Notation) is a widely used data format for APIs, configuration files, and data storage. However, parsing and manipulating JSON from the command line or scripts can be cumbersome without the right tools.

**jq** is a lightweight, powerful, and flexible command-line JSON processor that allows you to:

- **Filter, transform, and extract** data from JSON structures easily
- **Format and prettify** JSON for better readability
- **Perform complex operations** like sorting, mapping, and reducing JSON data
- **Integrate seamlessly** with shell scripts, APIs, and other command-line tools (e.g., `curl`)

## What is jq?

`jq` is a **stream-oriented** JSON processor that takes JSON input, applies transformations (defined by a *filter*), and produces JSON (or other formats) as output.

- **Written in C**: Fast and efficient
- **Available on most platforms**: Linux, macOS, and Windows (via WSL or native builds)
- **Open-source**: Licensed under the MIT license

## Key Features of jq

### 1. Simple Filtering
Extract specific fields from JSON:
```sh
echo '{"name": "Alice", "age": 30}' | jq '.name'
# Output: "Alice"
