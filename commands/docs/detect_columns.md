---
title: detect columns
categories: |
  strings
version: 0.82.0
strings: |
  Attempt to automatically split text into multiple columns.
usage: |
  Attempt to automatically split text into multiple columns.
---

# <code>{{ $frontmatter.title }}</code> for strings

<div class='command-title'>{{ $frontmatter.strings }}</div>

## Signature

```> detect columns --skip --no-headers --combine-columns```

## Parameters

 -  `--skip {int}`: number of rows to skip before detecting
 -  `--no-headers` `(-n)`: don't detect headers
 -  `--combine-columns {range}`: columns to be combined; listed as a range

## Examples

Splits string across multiple columns
```shell
> 'a b c' | detect columns -n
╭───┬─────────┬─────────┬─────────╮
│ # │ column0 │ column1 │ column2 │
├───┼─────────┼─────────┼─────────┤
│ 0 │ a       │ b       │ c       │
╰───┴─────────┴─────────┴─────────╯

```

Splits a multi-line string into columns with headers detected
```shell
> $'c1 c2 c3(char nl)a b c' | detect columns

```

Parse external ls command and combine columns for datetime
```shell
> ^ls -lh | detect columns --no-headers --skip 1 --combine-columns 5..7

```
