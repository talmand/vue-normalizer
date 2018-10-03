<template>
<div id="elements_content" v-on:mouseup="emitElementSelectedEvent">
    <div><a title="a" class="elements-item">anchor</a></div>
    <div><em title="em" class="elements-item">emphasis</em></div>
    <div><strong title="strong" class="elements-item">strong</strong></div>
</div>
</template>

<script>
export default {
  methods: {
    emitElementSelectedEvent: function (e) {
        if (e.target.classList.contains('elements-item')) {
            this.$root.$emit('element_selected', e.target);
        }
    }
  }
}
</script>

<style lang="scss">
$a: (
    background-color: transparent,
    border-color: transparent,
    border-radius: 0,
    border-style: none,
    border-width: 0,
    color: blue,
    display: inline,
    font-family: sans-serif,
    font-size: 1.2rem,
    font-style: normal,
    font-variant-caps: normal,
    font-weight: 500,
    line-height: 1.6em,
    list-style-type: none,
    margin: 0,
    padding: 0,
    text-align: left,
    text-decoration-color: blue,
    text-decoration-line: underline,
    text-decoration-style: solid,
    text-indent: 0
);

$em: (
    background-color: transparent,
    border-color: transparent,
    border-radius: 0,
    border-style: none,
    border-width: 0,
    color: #333,
    display: inline,
    font-family: sans-serif,
    font-size: 1.2rem,
    font-style: italic,
    font-variant-caps: normal,
    font-weight: 500,
    line-height: 1.6em,
    list-style-type: none,
    margin: 0,
    padding: 0,
    text-align: left,
    text-decoration-color: transparent,
    text-decoration-line: none,
    text-decoration-style: solid,
    text-indent: 0
);

$strong: (
    background-color: transparent,
    border-color: transparent,
    border-radius: 0,
    border-style: none,
    border-width: 0,
    color: #333,
    display: inline,
    font-family: sans-serif,
    font-size: 1.2rem,
    font-style: normal,
    font-variant-caps: normal,
    font-weight: 700,
    line-height: 1.6em,
    list-style-type: none,
    margin: 0,
    padding: 0,
    text-align: left,
    text-decoration-color: transparent,
    text-decoration-line: none,
    text-decoration-style: solid,
    text-indent: 0
);

:root {
    @each $property, $value in $a { #{'--a_' + $property}: $value; }
    @each $property, $value in $em { #{'--em_' + $property}: $value; }
    @each $property, $value in $strong { #{'--strong_' + $property}: $value; }
}

a { @each $property, $value in $a { #{$property}: var(#{'--a_' + $property}); } }
em { @each $property, $value in $em { #{$property}: var(#{'--em_' + $property}); } }
strong { @each $property, $value in $strong { #{$property}: var(#{'--strong_' + $property}); } }
</style>