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

### `padding` / `margin`

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

### `text size` / `font-family`

Zaftig Tailwind provides 3 basic `font-family` helpers, `font-sans`, `font-serif` and `font-mono`. Use to apply good looking web-safe fonts of the particular type.

The `text` helper provides a series of preset `font-size`s based on what [Tailwind CSS provides](). It accepts a single argument specifying the size which can be: `xs`, `sm`, `base`, `lg`, `xl`, `2xl`, `3xl`, `4xl`, `5xl`, or `6xl`.

```js
z`
  font-sans
  text xl
`
```

### `shadow`

Applies a given intensity/type of box-shadow. This helper takes one param which is one of the following values: `base`, `md`, `lg`, `xl`, `2xl`, `inner`, `outline`, `none`.

```js
z`shadow lg`
// box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
```

### `rounded`

This helper doesn't take params and simply applies `0.25rem` of border-radius.

```js
z`rounded`
// border-radius: 0.25rem;
```

### `size`

This helper takes 2 params, `width` and `height` in `px` if not specified. If only 1 param is provided the same value will be used for both `width` and `height`.

```js
z`
  size 40
  size 100 200
  size 20rem
`
```

## Colors

Tailwind's whole palette of colors are provided as css variables. Since they're variables they can easily be used with any CSS property.

[See here for the full list of available colors](https://tailwindcss.com/docs/customizing-colors#default-color-palette).

The color variables are not loaded by default, allowing you to import them and load them at whatever scope you like.

```js
import { colors } from 'zaftig-tailwind'

// load the colors into the global scope
z.global(colors)

// use them in a style
z`
  color $blue-2
  background-color $green-5
  border 1 solid $red-5
`
```

Since the colors are just css variables you can easily redefine them as follows:

```js
import { colors } from 'zaftig-tailwind'

// load colors into global scope and redefine blue-2
z.global`
  ${colors}
  
  $blue-2 #4299E1
`
```

## Customization

The defaults provided by this library can easily be changed if so desired. Several of the value maps are exported by the library and can simply be mutated.

```js
import { breakpoints, shadowMap, textSizes } from 'zaftig-tailwind'

breakpoints.md = '900px'
shadowMap.outline = '0 0 0 10px rgba(66, 153, 225, 0.5)'
textSizes.lg = '1.5rem'
```

The properties of the object matchup to the possible values of the relevant helpers.
