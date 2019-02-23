<template>
  <div class="container mt-3">
    <p v-show="!getWishList.length" class="text-center p-3">Нямате добавени книги в желани!</p>
    <div class="row mb-3" v-if="getWishList.length">
      <st-book-item
        v-for="(book) in getWishList"
        :key="book.id"
        :id="book.id"
        :title="book.volumeInfo.title"
        :description="book.volumeInfo.description"
        :author="book.volumeInfo.author"
        :image="book.volumeInfo.imageLinks"
        :year="book.volumeInfo.publishedDate"
        :rating="book.volumeInfo.averageRating"
        @displayModal="displayModal"
      ></st-book-item>
    </div>
  </div>
</template>

<script>
  import StSearchFilter from '../common/SearchFilter';
  import StBookItem from '../common/BookItem';
  import StSelectRating from '../common/Rating';

  export default {
    name: 'wish-list',
    components: {
      StSearchFilter,
      StBookItem,
      StSelectRating,
    },
    computed: {
      getWishList() {
        const wishlist = this.$store.state.wishList;
        return wishlist;
      },
      getCurrentMovieTitle(){
        if(!this.$store.state.currentBook){
          return '';
        }
        return this.$store.state.currentBook.volumeInfo.title;
      }
    },

  };
</script>
