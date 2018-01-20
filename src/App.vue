<template>
    <div class="container">
        <template v-if="!showGame">
            <progres-bar :quotes-length="quotes.length" :max-quotes="maxQuotes"></progres-bar>
            <quote-create @createQuote="create"></quote-create>
            <quote-grid :quotes-list="quotes" @quoteDeleted="deleteQuote"></quote-grid>
            <div class="row">
                <div class="col-sm-12 text-center">
                    <div class="alert alert-info">Info: Click on a Quote to Delete it!</div>
                </div>
            </div>
        </template>
        <template v-if="showGame">
            <monster-game></monster-game>
        </template>
        <button class="btn btn-primary" @click="showGame = !showGame">Show Monster game</button>
    </div>
</template>

<script>
import QuoteGrid from './components/QuoteGrid.vue'
import QuoteCreate from './components/QuoteCreate.vue'
import ProgresBar from './components/ProgresBar.vue'
import MonsterGame from './components/MonsterGame.vue'


    export default {
        data() {
        	return {
        		quotes: [],
                maxQuotes: 10,
                showGame: false
        	}
        },
        methods: {
            create(value) {
                if (this.quotes.length < this.maxQuotes) {
                    this.quotes.push(value);
                } else {
                    alert(`Max Quotes number is ${ this.maxQuotes }!`)
                }
            },
            deleteQuote(quoteIndex) {
                this.quotes.splice(quoteIndex, 1);
            }
        },
        components: {
        	'quote-grid': QuoteGrid,
            'quote-create': QuoteCreate,
            'progres-bar': ProgresBar,
            'monster-game': MonsterGame
        }
    }
</script>
