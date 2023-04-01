<template>
  <tr class="table-item__table-row">
    <td>{{ title }}</td>
    <td>{{ author }}</td>
    <td>{{ isbn }}</td>
    <td>{{ numPages }}</td>
    <td>
      <BaseButton
        :text="bookMarkedButtonText"
        variant="primary"
        @button-clicked="handleBookMarkButtonClick"
      />
    </td>
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
    numPages: Number,
    isBookmarked: Boolean,
  },
  data() {
    return {
      baseButtonText: "Add Bookmark",
    };
  },
  computed: {
    bookMarkedButtonText() {
      return this.isBookmarked ? "Remove Bookmark" : "Add Bookmark";
    },
  },
  emits: ["bookmark-clicked"],
  methods: {
    handleBookMarkButtonClick() {
      this.$emit("bookmark-clicked", this.isbn);
      console.log(this.isbn);
    },
  },
};
</script>

<style scoped>
.table-item__table td {
  padding: 12px 15px;
}
</style>
