
<script setup lang="ts">
defineProps<{
  data: any;
  columns: {
    label: string;
    field: string;
  }[];
}>();

</script>

<template>
  <table class="w-[1000px]">
    <thead class="bg-gray-100">
      <tr class="border-b-[2px] border-gray-300">
        <th
          v-for="(column, index) in columns"
          :key="index"
          class="text-left  py-4 min-w-[80px]"
        >
          <div class="pl-4 " :class="{'border-l-[2px] border-gray-300': index}">{{ column.label }}</div>
        </th>
      </tr>
    </thead>
    <tbody>
      <tr  v-for="(item, index) in data" :key="index" class="border-b-[2px] border-gray-300 hover:bg-gray-50">
        <td  v-for="(column, cIndex) in columns" :key="cIndex" text-left pl-4 py-4>
          <div v-if="!(item[column.field] instanceof Array)">{{ item[column.field] }}</div>
          <div v-else v-for="(k, i) in item[column.field]" :key="i" v-html="k"></div>
        </td>
      </tr>
    </tbody>
  </table>
</template>


<style scoped>
</style>