<template>
  <section class="table-item">
    <h2 class="table-item__hl">{{ h2Text }}</h2>
    <table class="table-item__table">
      <thead>
        <tr>
          <th
            v-for="tableHeadColumn in tableHeadColumns"
            :key="tableHeadColumn"
            class="table-item__table-row"
          >
            {{ tableHeadColumn }}
          </th>
        </tr>
      </thead>
      <tbody>
        <book-list-row
          class="table-item__table-row"
          v-for="book in books"
          :key="book.isbn"
          :title="book.title"
          :author="book.author"
          :isbn="book.isbn"
          :numPages="book.numPages"
          :isBookmarked="book?.isBookmarked"
        >
          <template #actionCol="slotProps">
            <BaseButton
              :variant="secondary"
              @button-clicked="handleBookMarkClick(slotProps.isbn)"
            >
              <svg
                v-if="!slotProps?.isBookmarked"
                style="width: 18px; line-height: 1"
                xmlns="http://www.w3.org/2000/svg"
                class="h-5 w-5"
                viewBox="0 0 20 20"
                fill="currentColor"
              >
                <path
                  fill-rule="evenodd"
                  d="M10 18a8 8 0 100-16 8 8 0 000 16zm1-11a1 1 0 10-2 0v2H7a1 1 0 100 2h2v2a1 1 0 102 0v-2h2a1 1 0 100-2h-2V7z"
                  clip-rule="evenodd"
                />
              </svg>
              <svg
                v-else
                style="width: 18px; line-height: 1"
                xmlns="http://www.w3.org/2000/svg"
                class="h-5 w-5"
                viewBox="0 0 20 20"
                fill="currentColor"
              >
                <path
                  fill-rule="evenodd"
                  d="M10 18a8 8 0 100-16 8 8 0 000 16zM8.707 7.293a1 1 0 00-1.414 1.414L8.586 10l-1.293 1.293a1 1 0 101.414 1.414L10 11.414l1.293 1.293a1 1 0 001.414-1.414L11.414 10l1.293-1.293a1 1 0 00-1.414-1.414L10 8.586 8.707 7.293z"
                  clip-rule="evenodd"
                />
              </svg>
              {{ bookMarkedButtonText(slotProps?.isBookmarked) }}
            </BaseButton>
          </template>
        </book-list-row>
      </tbody>
    </table>
  </section>
</template>

<script>
import BookListRow from "@/components/BookListRow.vue";
import BaseButton from "@/components/BaseButton.vue";

export default {
  name: "BookListComponent",
  components: {
    BookListRow,
    BaseButton,
  },
  data() {
    return {
      h2Text: "Overview about All Books",
      tableHeadColumns: ["Title", "Author", "ISBN", "Pages", "Actions"],
      books: [
        {
          title: "Practical Rust Web Projects",
          isbn: "9781484265888",
          author: "Shing Lyu",
          publisher: "Apress",
          price: "$28.75",
          numPages: 256,
        },
        {
          title: "Using WebPagetest",
          isbn: "9781491902592",
          author: "Rick Viscomi, Andy Davies, Marcel Duran",
          publisher: "O'Reilly Media",
          price: "$25.80",
          numPages: 214,
        },
        {
          title: "Web Scraping with Python",
          isbn: "9781491910290",
          author: "Ryan Mitchell",
          publisher: "O'Reilly Media",
          price: "$14.00",
          numPages: 256,
        },
        {
          title: "High Performance Mobile Web",
          isbn: "9781491912553",
          author: "Maximiliano Firtman",
          publisher: "O'Reilly Media",
          price: "$7.00",
          numPages: 326,
        },
      ],
    };
  },
  methods: {
    bookMarkedButtonText(isBookmarked) {
      return isBookmarked ? "Remove Bookmark" : "Add Bookmark";
    },
    handleBookMarkClick(isbn) {
      const currentBookIndex = this.books.findIndex(
        (book) => book.isbn === isbn
      );
      const currentBook = this.books[currentBookIndex];
      currentBook.isBookmarked = !currentBook.isBookmarked ? true : false;
    },
  },
};
</script>

<style scoped>
.table-item__table {
  border-collapse: collapse;
  margin: 25px 0;
  font-size: 0.9em;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.15);
  width: 100%;
}
.table-item__table-head-name {
  width: 65%;
}
.table-item__table-head-isbn {
  width: 20%;
}
.table-item__table-head-actions {
  width: 15%;
}
.table-item__table-row button {
  opacity: 0;
  padding: 5px;
  transition: opacity 500ms;
  cursor: pointer;
  border-radius: 5px;
}

.table-item__table-row:hover button {
  opacity: 1;
}
.table-item__table thead tr {
  background-color: var(--primary);
  color: #ffffff;
  text-align: left;
}
.table-item__table th {
  padding: 12px 15px;
}
.table-item__table tbody tr {
  border-bottom: 1px solid #dddddd;
}
.table-item__table tbody tr:nth-of-type(even) {
  background-color: #f3f3f3;
}
.table-item__table tbody tr:last-of-type {
  border-bottom: 2px solid var(--primary);
}
.table-item__table tbody tr.active-row {
  font-weight: bold;
  color: var(--primary);
}
.table-item__hl {
  margin-top: 1rem;
  padding-bottom: 0.4rem;
  border-bottom: 2px solid var(--primary-dark);
}
</style>
