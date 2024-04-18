<script setup lang="ts">
interface treeDatatype {
  name: string
  children?: treeDatatype[]
  childIndex?: number
}
const treeData = ref<treeDatatype[]>([
  {
    name: 'Models',
    children: [
      {
        name: 'Data warehouse',
        children: [
          {
            name: 'Report samples',
            children: [
              { name: 'Report samples' },
              { name: 'Sales performance' },
            ],
          },
          {
            name: 'Sales performance',
            children: [
              { name: 'Report samples' },
              {
                name: 'Sales performance',
                children: [
                  { name: 'Report samples' },
                  {
                    name: 'Sales performance',
                    children: [
                      { name: 'Report samples' },
                      { name: 'Sales performance' },
                    ],
                  },
                ],
              },
            ],
          },
        ],
      },
    ],
  },
  {
    name: 'Statistics',
    children: [{ name: 'Element' }, { name: 'Element' }],
  },
])

const tableColumns = ref([
  {
    label: 'Name',
    field: 'name',
  },
  {
    label: 'Age',
    field: 'age',
  },
  {
    label: 'Address',
    field: 'address',
  },
  {
    label: 'Tags',
    field: 'tags',
  },
  {
    label: 'Action',
    field: 'action',
  },
])
const tableData = ref([
  {
    name: 'Jhon Brown',
    age: 32,
    address: 'New York No. 1 Lake Park',
    tags: [
      '<div class="bg-green-200 border-green-400 text-green-600 py-[1px] px-2 mx-1 font-size-[14px] rounded border" >NICE</div>',
      '<div class="bg-blue-200 border-blue-400 text-blue-600 py-[1px] px-2 mx-1 font-size-[14px] rounded border" >DEVELOPER</div>',
    ],
    action:
      '<h2 class="text-blue-600 px-1 border-gray-300 border-x-2 cursor-pointer">Delete</h2>',
  },
  {
    name: 'Jhon Brown',
    age: 32,
    address: 'New York No. 1 Lake Park',
    tags: [
      '<div class="bg-red-200 border-red-400 text-red-600 py-[1px] px-2 mx-1 font-size-[14px] rounded border" >LOSER</div>',
    ],
    action: [
      '<div class="text-blue-600 px-1 border-gray-300 border-l-2 cursor-pointer">Invite - Jhon Brown</div>',
      '<h2 class="text-blue-600 px-1 border-gray-300 border-x-2 cursor-pointer">Delete</h2>',
    ],
  },
  {
    name: 'Jhon Brown',
    age: 32,
    address: 'New York No. 1 Lake Park',
    tags: [
      '<div class="bg-green-200 border-green-400 text-green-600 py-[1px] px-2 mx-1 font-size-[14px] rounded border" >COOL</div>',
      '<div class="bg-blue-200 border-blue-400 text-blue-600 py-[1px] px-2 mx-1 font-size-[14px] rounded border" >TEACHER</div>',
    ],
    action: [
      '<div class="text-blue-600 px-1 border-gray-300 border-l-2 cursor-pointer">Invite - Jhon Brown</div>',
      '<h2 class="text-blue-600 px-1 border-gray-300 border-x-2 cursor-pointer">Delete</h2>',
    ],
  },
])
</script>

<template>
  <div flex flex-col items-center gap-2>
    <v-tree-collapse :tree-data="treeData" />
    <v-table :data="tableData" :columns="tableColumns" />
  </div>
</template>

<route lang="yaml">
meta:
  layout: default
</route>
