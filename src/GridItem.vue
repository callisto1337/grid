<template>
  <component :is="component" :style="styleProperties">
    <slot />
  </component>
</template>

<script lang="ts" setup>
import { computed, CSSProperties } from 'vue';
import { AlignContent, Columns } from './types';

export interface GridItemProps {
  size: Columns;
  alignSelf: AlignContent;
  component: string;
}

const props = withDefaults(defineProps<GridItemProps>(), {
  size: 1,
  alignSelf: 'auto',
  component: 'div',
});
const styleProperties = computed<CSSProperties>(() => {
  const size = props.size;
  const alignSelf = props.alignSelf;

  return {
    gridColumnStart: `span ${size}`,
    alignSelf,
  };
});
</script>
