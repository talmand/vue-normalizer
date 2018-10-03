<template>
<section id="panel_examples">
    <button v-on:mouseup="emitLoremIpsumEvent">lorem ipsum</button>
    <button v-on:mouseup="emitListsEvent">lists</button>
</section>
</template>

<script>
export default {
    methods: {
        emitLoremIpsumEvent: function () {
            this.$root.$emit('example_loremipsum');
        },
        emitListsEvent: function () {
            this.$root.$emit('example_lists');
        }
    }
}
</script>

<style lang="scss">

</style>