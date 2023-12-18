<script setup lang="ts">
defineProps<{
  data: any
  columns: {
    label: string
    field: string
  }[]
}>()
</script>

<template>
  <table class="w-[1000px]">
    <thead class="bg-gray-100">
      <tr class="border-b-[2px] border-gray-300">
        <th
          v-for="(column, index) in columns"
          :key="index"
          class="min-w-[80px] py-4 text-left"
        >
          <div
            class="pl-4"
            :class="{ 'border-l-[2px] border-gray-300': index }"
          >
            {{ column.label }}
          </div>
        </th>
      </tr>
    </thead>
    <tbody>
      <tr
        v-for="(item, index) in data"
        :key="index"
        class="border-b-[2px] border-gray-300 hover:bg-gray-50"
      >
        <td
          v-for="(column, cIndex) in columns"
          :key="cIndex"

          py-4 pl-4 text-left
        >
          <div flex>
            <div
              v-if="!(Array.isArray(item[column.field]))"
              v-html="item[column.field]"
            />
            <div
              v-for="(k, i) in item[column.field]"
              v-else
              :key="i"
              v-html="k"
            />
          </div>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<style scoped>
</style>
