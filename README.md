# @vuelib/grid

Simple zero-dependency grid for Vue 3

# Installation

```
npm i @vuelib/grid
```

## Example

```vue
<template>
  <Grid :spacing="['8px', '16px']">
    <GridItem :size="6">First item</GridItem>
    <GridItem :size="6">Second item</GridItem>
    <GridItem :size="12">Third item</GridItem>
  </Grid>
</template>

<script lang="ts" setup>
import { Grid, GridItem } from '@vuelib/grid';
</script>
```

## Props

### Grid

|     Name     |                         Type                          |   Default   |
|:------------:|:-----------------------------------------------------:|:-----------:|
|  `spacing`   |             `string \| [string, string?]`             |   `'0px'`   |
|  `columns`   |                  `number \| string`                   |    `12`     |
| `alignItems` | `'start' \| 'center' \| 'end' \| 'stretch' \| 'auto'` | `'stretch'` |
| `component`  |                       `string`                        |   `'div'`   |

### GridItem

|    Name     |                         Type                          | Default  |
|:-----------:|:-----------------------------------------------------:|:--------:|
|   `size`    |                  `number \| string`                   |   `1`    |
| `alignSelf` | `'start' \| 'center' \| 'end' \| 'stretch' \| 'auto'` | `'auto'` |
| `component` |                       `string`                        | `'div'`  |

## License

[MIT](LICENSE)
