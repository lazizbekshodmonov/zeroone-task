<script setup lang="ts">
interface treeDatatype {
  name: string
  children?: treeDatatype[]
}
const { treeData, childIndex } = withDefaults(
  defineProps<{
    treeData?: treeDatatype[]
    childIndex?: number
  }>(),
  {
    childIndex: 0,
  },
)

const chIndex = ref(childIndex || 0)

chIndex.value = childIndex + 10

const collapsedItems = ref<number[]>([])

function toggle(index: number) {
  if (collapsedItems.value?.includes(index)) {
    collapsedItems.value = collapsedItems.value.filter(
      item => item !== index,
    )
  }
  else {
    collapsedItems.value?.push(index)
  }
}
</script>

<template>
  <ul :class="[{ 'w-[400px] rounded bg-gray-200': chIndex === 10 }]">
    <li v-for="(item, index) in treeData" :key="index">
      <div
        class="my-1 cursor-pointer border-l-[4px] py-1 pl-1 hover:border-blue hover:bg-gray-300"
        @click="toggle(index)"
      >
        <div
          flex
          items-center
          text-left
          :style="{ paddingLeft: `${chIndex}px` }"
        >
          <div
            v-if="item.children"
            i-carbon-caret-down
            class="rotate-[-90deg] transition"
            :class="[collapsedItems?.includes(index) ? 'rotate-0' : '']"
          />
          <p :class="{ 'ml-5': !item.children }">
            {{ item.name }}
          </p>
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
