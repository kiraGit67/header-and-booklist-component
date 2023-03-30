<template>
  <header-component />
  <book-list-component />
</template>

<script>
import HeaderComponent from "@/components/HeaderComponent.vue";
import BookListComponent from "@/components/BookListComponent.vue";

export default {
  name: "App",
  components: {
    HeaderComponent,
    BookListComponent,
  },
};
</script>
