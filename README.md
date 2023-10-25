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
