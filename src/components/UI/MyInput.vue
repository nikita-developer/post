<template>
    <input :value="modelValue" @input="updateInput" class="input" type="text">
</template>

<script>
    export default {
        name: 'MyInput',
        props: {
            modelValue: [String, Number]
        },
        methods: {
            updateInput(e) {
                this.$emit('update:modelValue', e.target.value)
            }
        }
    }
</script>

<style lang="scss" scoped>
    .input {
        display: block;
        width: 100%;
        padding: .5em;
        border: 1px solid #d7d7d7;

        &:focus {
            outline: 0;
            border-color: #b8d9f5;
            color: #747474;
        }
    }
</style>