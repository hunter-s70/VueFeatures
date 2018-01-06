<template>
	<div class="row">
		<quote v-for="quote in quotesList">{{ quote }}</quote>
	</div>
</template>

<script>
import Quote from '../components/Quote.vue'

    export default {
    	props: ['quotesList'],
        data() {
        	return {
        		numbers: [ 1, 2, 3, 4, 5 ],
        		quotes: '123456'
        	}
        },
        components: {
        	'quote': Quote
        },
        mounted() {
        	console.log(this.quotesList);
        }
    }
</script>

<style>
</style>