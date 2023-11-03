<template>
  <div class="container">
    <Grid spacing="10px" row-spacing="20px">
      <GridItem :size="6">
        <div class="item" />
      </GridItem>
      <GridItem :size="5" :offset="1">
        <div class="item" />
      </GridItem>
      <GridItem :size="12">
        <div class="item" />
      </GridItem>
    </Grid>
  </div>
</template>

<script lang="ts" setup>
import { Grid, GridItem } from '../';
</script>

<style>
body {
  background-color: #f3f6f9;
}

.item {
  background-color: #ffffff;
  box-shadow:
    0 2px 1px -1px rgba(0, 0, 0, 0.2),
    0 1px 1px 0 rgba(0, 0, 0, 0.14),
    0 1px 3px 0 rgba(0, 0, 0, 0.12);
  border-radius: 4px;
  min-height: 50px;
}
</style>
