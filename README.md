# Zaftig Tailwind

> ⚠ These docs are a WIP ⚠

A helper library for [Zaftig](https://github.com/fuzetsu/zaftig) (CSS in JS) that brings some of the main utilities from [Tailwind CSS](https://tailwindcss.com/).

## Example Usage

```js
import z from 'zaftig'
import { colors, helpers } from 'zaftig-tailwind'

z.global(colors) // register color variables
z.helper(helpers) // register helpers

z.global`
  font-sans
  c $gray-8
  pad 3

  @between sm md {
    a { c $green-5 }
  }
`
```

# Features

## Helpers

### padding / margin

Tailwind CSS provides utilities to set padding/margin in increments of `0.25rem`.

You achieve the same using the helpers `mar` / `pad`

The first argument to the helper is a number and will be multiplied by `0.25rem`, the second optional argument is the directions to apply the margin/padding to. `t` is top, `b` is bottom, `l` is left, and `r` is right.

```
pad 3     === padding: 0.75rem
mar 10    === margin: 2.5rem
pad 2 lrt === padding-left: 0.5rem; padding-right: 0.5rem; padding-top: 0.5rem
```

```js
z`
  pad 3
  mar 10

  pad 3 lr
  mar 10 tlr
`
```

### font / font-size

Zaftig Tailwind provides 3 basic `font-family` helpers, `font-sans`, `font-serif` and `font-mono`. Use to apply good looking web-safe fonts of the particular type.

The `text` helper provides a series of preset `font-size`s based on what [Tailwind CSS provides](). It accepts a single argument specifying the size which can be: xs ,sm, base, lg, xl, 2xl, 3xl, 4xl, 5xl, or 6xl.

```js
z`
  font-sans
  text xl
`
```

### border-radius / box-shadow



### Misc

## Colors

## Customization
