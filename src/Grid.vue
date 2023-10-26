<template>
  <component :is="component" :style="styleProperties">
    <slot />
  </component>
</template>

<script lang="ts" setup>
import { CSSProperties, computed } from 'vue';

export interface GridProps {
  columnSpacing: string;
  rowSpacing: string;
  component: string;
  direction: 'column' | 'column-reverse' | 'row' | 'row-reverse';
  columns: number;
  wrap: 'nowrap' | 'wrap' | 'wrap-reverse';
  justifyContent: 'space-around' | 'space-between' | 'space-evenly' | 'center' | 'left' | 'start';
  alignItems: 'start' | 'center' | 'end' | 'stretch';
}

const props = withDefaults(defineProps<GridProps>(), {
  columnSpacing: '0px',
  rowSpacing: '0px',
  component: 'div',
  direction: 'row',
  columns: 12,
  wrap: 'wrap',
  justifyContent: 'start',
  alignItems: 'start',
});

const styleProperties = computed<CSSProperties>(() => {
  const columnSpacing = props.columnSpacing;
  const rowSpacing = props.rowSpacing;

  const properties: CSSProperties = {
    flexDirection: props.direction,
    flexWrap: props.wrap,
    alignItems: props.alignItems,
    justifyContent: props.justifyContent,
    display: 'flex',
    marginLeft: `calc(-${columnSpacing} / 2)`,
    marginRight: `calc(-${columnSpacing} / 2)`,
    marginTop: `calc(-${rowSpacing} / 2)`,
    marginBottom: `calc(-${rowSpacing} / 2)`,
  };

  return properties;
});
</script>
