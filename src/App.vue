<template>
    <div class="container">
        <quote-create @createQuote="create"></quote-create>
    	<quote-grid :quotes-list="quotes"></quote-grid>
    </div>
</template>

<script>
import QuoteGrid from './components/QuoteGrid.vue'
import QuoteCreate from './components/QuoteCreate.vue'

    export default {
        data() {
        	return {
        		quotes: [],
                maxQuotes: 10
        	}
        },
        methods: {
            create(value) {
                if (this.quotes.length < this.maxQuotes) {
                    this.quotes.push(value);
                } else {
                    alert('Max Quotes number is 10!')
                }
            }
        },
        components: {
        	'quote-grid': QuoteGrid,
            'quote-create': QuoteCreate
        }
    }
</script>

<style>
</style>
