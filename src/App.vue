<template>
    <div class="container">
    	<quote-grid></quote-grid>
    </div>
</template>

<script>
import QuoteGrid from './components/QuoteGrid.vue'

    export default {
        data() {
        	return {
        		quotes: []
        	}
        },
        components: {
        	'quote-grid': QuoteGrid
        }
    }
</script>

<style>
</style>
