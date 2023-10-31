<template>
  <component :is="component" :style="styleProperties">
    <slot />
  </component>
</template>

<script lang="ts" setup>
import { CSSProperties, computed } from 'vue';
import { AlignContent, Columns } from './types';

export interface GridProps {
  spacing: string | [string, string?];
  columns: Columns;
  alignItems: AlignContent;
  component: string;
}

const props = withDefaults(defineProps<GridProps>(), {
  spacing: '0',
  columns: 12,
  alignItems: 'stretch',
  component: 'div',
});

function getGap(spacing: GridProps['spacing']): string {
  if (Array.isArray(spacing)) {
    return [spacing[0], spacing[1]].filter(Boolean).join(' ');
  }

  return spacing;
}

const styleProperties = computed<CSSProperties>(() => {
  const columns = props.columns;
  const spacing = props.spacing;
  const alignItems = props.alignItems;

  const properties: CSSProperties = {
    display: 'grid',
    gap: getGap(spacing),
    gridTemplateColumns: `repeat(${columns}, 1fr)`,
    alignItems,
  };

  return properties;
});
</script>
