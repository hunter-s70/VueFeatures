<template>
    <div class="container">
        <quote-create></quote-create>
    	<quote-grid :quotes-list="quotes"></quote-grid>
    </div>
</template>

<script>
import QuoteGrid from './components/QuoteGrid.vue'
import QuoteCreate from './components/QuoteCreate.vue'

    export default {
        data() {
        	return {
        		quotes: ['first step', 'second-quo', 'вавава', 'вавава', 'вавава', 'вавава', 'вавава', 'вавава']
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
