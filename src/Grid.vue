<template>
  <component :is="component" :style="styleProperties">
    <slot />
  </component>
</template>

<script lang="ts" setup>
import { CSSProperties, computed } from 'vue';

export interface GridProps {
  spacing: CSSProperties['gap'];
  columnSpacing: CSSProperties['column-gap'];
  rowSpacing: CSSProperties['row-gap'];
  component: keyof HTMLElementTagNameMap;
  direction: CSSProperties['flex-direction'];
  columns: number;
  wrap: CSSProperties['flex-wrap'];
  justifyContent?: CSSProperties['justify-content'];
  alignItems?: CSSProperties['align-items'];
}

const props = withDefaults(defineProps<GridProps>(), {
  spacing: 0,
  columnSpacing: 0,
  rowSpacing: 0,
  component: 'div',
  direction: 'row',
  columns: 12,
  wrap: 'wrap',
});

const styleProperties = computed<CSSProperties>(() => {
  const spacing = props.spacing;
  const columnSpacing = props.columnSpacing || spacing;
  const rowSpacing = props.rowSpacing || spacing;

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
