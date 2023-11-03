<template>
  <Grid spacing="8px" column-spacing="10px">
    <GridItem :size="6">First item</GridItem>
    <GridItem :size="6">Second item</GridItem>
    <GridItem :size="12">Third item</GridItem>
  </Grid>
</template>

<script lang="ts" setup>
import { Grid, GridItem } from '../';
</script>

<style>
body {
  margin: 0;
}
</style>
