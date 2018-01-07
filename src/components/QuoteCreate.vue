<template>
    <div class="row quote-create">
        <div class="form-group col-sm-12">
          <label for="comment">Quote:</label>
          <textarea class="form-control quote-create__enter-field"
                    rows="5"
                    id="comment"
                    v-model="quoteText"></textarea>
        </div>
        <div class="col-sm-12">
            <button class="btn btn-primary btn-block" @click="sendQuote">Send</button>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
        	return {
        		quoteText: ''
        	}
        },
        methods: {
            sendQuote() {
                if (this.quoteText.trim()) {
                    this.$emit('createQuote', this.quoteText);
                    this.quoteText = '';
                }
            }
        }
    }
</script>

<style scoped>
.quote-create {
    margin-bottom: 20px;
}
</style>