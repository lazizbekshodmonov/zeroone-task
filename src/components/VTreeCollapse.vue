<script setup lang="ts">
interface treeDatatype {
  name: string;
  children?: treeDatatype[];
}
const { treeData, childIndex } = withDefaults(
  defineProps<{
    treeData?: treeDatatype[];
    childIndex?: number;
  }>(),
  {
    childIndex: 0,
  }
);

const chIndex = ref(childIndex ? childIndex : 0);

chIndex.value = childIndex + 10;

const collapsedItems = ref<number[]>([]);

function toggle(index: number) {
  if (collapsedItems.value?.includes(index)) {
    collapsedItems.value = collapsedItems.value.filter(
      (item) => item !== index
    );
  } else {
    collapsedItems.value?.push(index);
  }
}
</script>

<template>
  <ul :class="{'w-[400px] rounded bg-gray-200': chIndex == 10}">
    <li v-for="(item, index) in treeData" :key="index">
      <div
        @click="toggle(index)"
        class=" hover:bg-gray-300 cursor-pointer my-1 border-l-[4px] pl-1 py-1 hover:border-blue"
      >
        <div flex items-center text-left :style="{ paddingLeft: chIndex + 'px' }">
          <div v-if="item.children" i-carbon-caret-down class="transition rotate-[-90deg]" :class="collapsedItems?.includes(index) ? 'rotate-0' : ''" />
          <p :class="{'ml-5': !item.children}">{{ item.name }}</p>
        </div>
      </div>
      <div v-if="item.children && collapsedItems?.includes(index)" class="">
        <v-tree-collapse :tree-data="item.children" :child-index="chIndex" />
      </div>
    </li>
  </ul>
</template>



<style scoped>
</style>