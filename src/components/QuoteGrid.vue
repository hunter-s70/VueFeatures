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
        	}
        },
        components: {
        	'quote': Quote
        }
    }
</script>

<style>
</style>