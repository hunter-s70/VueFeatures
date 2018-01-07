<template>
    <div class="row">
        <div class="col-sm-12">
            <div class="progress progress-quotes">
              <div class="progress-bar" role="progressbar" aria-valuenow="70"
              aria-valuemin="0" aria-valuemax="100" :style="{'width': (quotesLength / maxQuotes) * 100 + '%'}">
                {{ quotesLength }}/{{ maxQuotes }}
              </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['maxQuotes', 'quotesLength']
    }
</script>

<style scoped>
.progress-quotes {
    margin-top: 20px;
}
</style>