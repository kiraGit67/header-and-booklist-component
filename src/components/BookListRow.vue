<template>
  <tr class="table-item__table-row">
    <td>{{ title }}</td>
    <td>{{ author }}</td>
    <td>{{ isbn }}</td>
    <td>{{ numPages }}</td>
    <td><BaseButton text="Add Bookmark" /></td>
  </tr>
</template>

<script>
import BaseButton from "@/components/BaseButton.vue";

export default {
  components: {
    BaseButton,
  },
  props: {
    title: String,
    author: String,
    isbn: String,
    numPages: String,
  },
};
</script>

<style scoped>
.table-item__table td {
  padding: 12px 15px;
}
</style>
