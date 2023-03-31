<template>
  <header-component />
  <main>
    <div id="app" class="inside">
      <book-list-component />
    </div>
  </main>
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
