<template>
  <component :is="component" :style="styleProperties">
    <slot />
  </component>
</template>

<script lang="ts" setup>
import { CSSProperties, computed, provide } from 'vue';
import { AlignContent, Columns, Spacing } from './types';

export interface GridProps {
  spacing: Spacing;
  rowSpacing: Spacing;
  columnSpacing: Spacing;
  columns: Columns;
  alignItems: AlignContent;
  component: string;
}

const props = withDefaults(defineProps<GridProps>(), {
  spacing: 0,
  rowSpacing: 0,
  columnSpacing: 0,
  columns: 12,
  alignItems: 'stretch',
  component: 'div',
});

function parseSpacingValue(spacing: Spacing): string {
  if (typeof spacing === 'string') {
    if (isNaN(Number(spacing))) {
      return spacing;
    }
  }

  return `${spacing}px`;
}

const rowSpacing = computed<string>(() => {
  return parseSpacingValue(props.rowSpacing || props.spacing);
});
const columnSpacing = computed<string>(() => {
  return parseSpacingValue(props.columnSpacing || props.spacing);
});
const styleProperties = computed<CSSProperties>(() => {
  const alignItems = props.alignItems;

  const properties: CSSProperties = {
    display: 'flex',
    flexWrap: 'wrap',
    margin: `calc(${rowSpacing.value} / -2) calc(${columnSpacing.value} / -2)`,
    alignItems,
  };

  return properties;
});

provide('columns', props.columns);
provide('rowSpacing', rowSpacing.value);
provide('columnSpacing', columnSpacing.value);
</script>
