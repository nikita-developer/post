<template>
    <button class="button">
        <slot></slot>
    </button>
</template>

<script>
    export default {
        name: 'MyButton'
    }
</script>

<style lang="scss" scoped>

    .button {
        padding: .5em 1.5em;
        background-color: #fff;
        border: 1px solid #d7d7d7;
        color: #747474;
        cursor: pointer;

        &:hover {
            background-color: #f3f3f3;
            color: #000;
        }
    }
</style>