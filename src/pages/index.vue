<script setup lang="ts">
interface treeData {
  name: string;
  children?: treeData[];
  childIndex?: number;
}
const treeData = ref<treeData[]>([
  {
    name: "Models",
    children: [
      {
        name: "Data warehouse",
        children: [{ name: "Report samples" }, { name: "Sales performance" }],
      },
    ],
  },
  {
    name: "Statistics",
    children: [{ name: "Element" }, { name: "Element" }],
  },
]);

const tableColumns = ref([
  {
    label: "Name",
    field: "name",
  },
  {
    label: "Age",
    field: "age",
  },
  {
    label: "Address",
    field: "address",
  },
  {
    label: "Tags",
    field: "tags",
  },
  {
    label: "Action",
    field: "action",
  },
]);
const tableData = ref([
  {
    name: "Jhon Brown",
    age: 32,
    address: "New York No. 1 Lake Park",
    tags: ["NICE", "DEVELOPER", ],
    action: ["Invite", "Delete"]
  },
  {
    name: "Jhon Brown",
    age: 32,
    address: "New York No. 1 Lake Park",
    tags: ["LOSER", "COOL"],
    action: ["Invite", "Delete"]
  },
  {
    name: "Jhon Brown",
    age: 32,
    address: "New York No. 1 Lake Park",
    tags: ['<h2>COOL</h2><div style="padding: 2px; background-color: aqua; border: 2px solid red; border-radius: 4px;">COOL</div>', "<h2>TEACHER</h2>"],
    action: ['<h2 style="color: blue;">Invite</h2>', '<h2 style="color: blue;">Delete</h2>']
  },
]);
</script>

<template>
  <div>
    <v-tree-collapse :tree-data="treeData" />
    <v-table :data="tableData" :columns="tableColumns" />
  </div>
</template>

<route lang="yaml">
meta:
  layout: default
</route>
