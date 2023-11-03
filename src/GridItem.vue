<template>
  <component :is="component" :style="styleProperties">
    <slot />
  </component>
</template>

<script lang="ts" setup>
import { computed, CSSProperties, inject } from 'vue';
import { AlignContent, Columns } from './types';

export interface GridItemProps {
  size: Columns;
  offset: Columns;
  alignSelf: AlignContent;
  component: string;
}

const props = withDefaults(defineProps<GridItemProps>(), {
  size: 1,
  offset: 0,
  alignSelf: 'auto',
  component: 'div',
});
const columns = inject('columns');
const rowSpacing = inject('rowSpacing');
const columnSpacing = inject('columnSpacing');
const styleProperties = computed<CSSProperties>(() => {
  const size = props.size;
  const offset = props.offset;
  const alignSelf = props.alignSelf;

  return {
    width: `calc(100% * ${size} / ${columns})`,
    padding: `calc(${rowSpacing} / 2) calc(${columnSpacing} / 2)`,
    marginLeft: `calc(100% * ${offset} / ${columns})`,
    boxSizing: 'border-box',
    alignSelf,
  };
});
</script>
