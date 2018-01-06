<template>
    <div class="quote-wrapp col-sm-6 col-md-4 col-lg-3">
        <div class="quote">
            <p class="quote__text">
                <slot></slot>
            </p>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
            }
        }
    }
</script>

<style scoped>
    .quote-wrapp {
        padding: 10px;
    }
    .quote {
        min-height: 100px;
        margin: ;
        padding: 8px;
        background: #efefef;
        border: 1px solid #000;
        border-radius: 4px;
    }
    .quote:hover {
        background: #ffe2e2;
    }
    .quote__text {
        font: 24px 'Arizonia', cursive;
    }
</style>