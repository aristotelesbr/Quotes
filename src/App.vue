<template>
  <div class="container">
    <AppHeader :quoteCount="quotes.length" :maxQuotes="maxQuotes"></AppHeader>
    <AppNewQuote @quoteAdded="newQuote"></AppNewQuote>
    <AppQuoteGrid :quotes="quotes" @quoteDeleted="deleteQuote"></AppQuoteGrid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">
          Info. Click on quote to delete it!
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import AppQuoteGrid from './components/QuoteGrid.vue'
  import AppNewQuote from './components/NewQuote.vue'
  import AppHeader from './components/Header.vue'

  export default {
   	data() {
   		return {
   			quotes: ['My first quote'],
   			maxQuotes: 10,
   		}
    },
    components: { AppQuoteGrid, AppNewQuote, AppHeader },
    methods: {
      newQuote(quote) {
        if (this.quotes.length >= this.maxQuotes ) {
          return alert('please delete quotes')
        }
        this.quotes.push(quote)
      },
      deleteQuote(index) {
        this.quotes.splice(index, 1)
      }
    }
  }
</script>

<style>
</style>
