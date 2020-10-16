 <template>
  <form v-on:submit.prevent="bookSubmit(bookTitle, bookAuthor)" class="" action="#" method="post">
    <input v-model="bookTitle" type="text" name="title" value="" placeholder="Book Title">
    <input v-model="bookAuthor" type="text" name="author" value="" placeholder="Book Author">
  <form v-on:submit.prevent="bookSubmit(bookData)" class="" action="#" method="post">
    <input v-model.trim="bookData.bookTitle" type="text" name="title" value="" placeholder="Book Title">
    <input v-model.trim="bookData.bookAuthor" type="text" name="author" value="" placeholder="Book Author">
    <div>
      <div>
        <textarea v-model="bookData.notes" type="text-area" rows="10" col="50"></textarea>
      </div>
      <div>
        <label for="finishedReading">
          Finished Reading
          <input v-model="bookData.finishedReading" type="checkbox" name="finishedReading" value="">
        </label>
      </div>
    </div>
    <div>
    <label for="borrowed">
      borrowed
      <input v-model="bookData.ownership" type="radio" id="borrowed" value="borrowed">
    </label>
    <label for="bought">
      bought
      <input v-model="bookData.ownership" type="radio" id="bought" value="bought">
    </label>
    </div>
    <button type="submit" name="button">Add Book</button>
  </form>
</template>
<script>
export default {
  name: "BookForm",
  props: ["books"],
  data() {
    return {
      bookTitle: "",
      bookAuthor: ""
      bookData: {
        bookTitle: "",
        bookAuthor: "",
        finishedReading: false,
        notes: "My notes about the book:",
        ownership: []
      }
    };
  },
  methods: {
    bookSubmit(bookTitle, bookAuthor) {
      this.$emit("addBook", bookTitle, bookAuthor);
    bookSubmit(bookData) {
      this.$emit("addBook", bookData);
    }
  }
};
</script>
<style>
</style>
