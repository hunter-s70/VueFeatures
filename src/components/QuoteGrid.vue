<template>
	<div class="row">
		<quote v-for="(quote, index) in quotesList" @click.native="deleteQuote(index)">{{ quote }}</quote>
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
        methods: {
        	deleteQuote(index) {
                this.$emit('quoteDeleted', index);
            }
        },
        components: {
        	'quote': Quote
        }
    }
</script>