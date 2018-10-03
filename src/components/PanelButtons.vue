<template>
<section id="panel_buttons">
    <button v-on:mouseup="emitBoxModelEvent">boxModel</button>
    <button v-on:mouseup="emitExamplesEvent">examples</button>
    <button v-on:mouseup="emitPropertiesEvent">properties</button>
    <button v-on:mouseup="emitScssExport">export</button>
    <button v-on:mouseup="emitImportEvent">import</button>
</section>
</template>

<script>
export default {
    methods: {
        emitBoxModelEvent: function () {
            this.$root.$emit('boxmodel_toggle');
        },
        emitExamplesEvent: function () {
            this.$root.$emit('examples_toggle');
        },
        emitPropertiesEvent: function () {
            this.$root.$emit('properties_toggle');
        },
        emitScssExport: function () {
            this.$root.$emit('export_scss');
        },
        emitImportEvent: function () {
            this.$root.$emit('click_import');
        }
    }
}
</script>

<style lang="scss">

</style>