# @vuelib/grid

Simple zero-dependency grid for Vue 3

# Installation

```
npm i @vuelib/grid
```

## Example

```vue
<template>
  <Grid spacing="10px">
    <GridItem :size="4">First item</GridItem>
    <GridItem :size="4">Second item</GridItem>
  </Grid>
</template>

<script lang="ts" setup>
import { Grid, GridItem } from '@vuelib/grid';
</script>
```

## Props

### Grid

|       Name       |                                         Type                                         |  Default  |
|:----------------:|:------------------------------------------------------------------------------------:|:---------:|
|    `spacing`     |                                       `string`                                       |  `'0px'`  |
| `columnSpacing`  |                                       `string`                                       |  `'0px'`  |
|   `rowSpacing`   |                                       `string`                                       |  `'0px'`  |
|   `component`    |                                       `string`                                       |  `'div'`  |
|   `direction`    |               `'column' \| 'column-reverse' \| 'row' \| 'row-reverse'`               |  `'row'`  |
|    `columns`     |                                       `number`                                       |   `12`    |
|      `wrap`      |                        `'nowrap' \| 'wrap' \| 'wrap-reverse'`                        | `'wrap'`  |
| `justifyContent` | `'start \| 'center' \| 'end' \| 'space-around' \| 'space-between' \| 'space-evenly'` | `'start'` |
|   `alignItems`   |                     `'start' \| 'center' \| 'end' \| 'stretch'`                      | `'start'` |

### GridItem

|    Name     |   Type   | Default |
|:-----------:|:--------:|:-------:|
|   `size`    | `number` |   `1`   |
| `component` | `string` | `'div'` |

## License

[MIT](LICENSE)
