<template>
  <component :is="component" :style="styleProperties">
    <slot />
  </component>
</template>

<script lang="ts" setup>
import { getCurrentInstance, computed, CSSProperties } from 'vue';
import { GridProps } from './';

export interface GridItemProps {
  size: number;
  component: string;
}

const props = withDefaults(defineProps<GridItemProps>(), {
  size: 1,
  component: 'div',
});
const instance = getCurrentInstance();
const styleProperties = computed<CSSProperties>(() => {
  const parentProps = instance?.parent?.props as unknown as GridProps;
  const columns = parentProps.columns;
  const spacing = parentProps.spacing;
  const columnSpacing = parentProps.columnSpacing || spacing;
  const rowSpacing = parentProps.rowSpacing || spacing;

  const properties: CSSProperties = {
    width: `calc(${(props.size / columns) * 100 + '%'} - ${columnSpacing})`,
    marginLeft: `calc(${columnSpacing} / 2)`,
    marginRight: `calc(${columnSpacing} / 2)`,
    marginTop: `calc(${rowSpacing} / 2)`,
    marginBottom: `calc(${rowSpacing} / 2)`,
  };

  return properties;
});
</script>
