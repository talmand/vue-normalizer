<template>
<div id="elements_sections" v-on:mouseup="emitElementSelectedEvent">
    <address title="address" class="elements-item">
        address<br />
        address<br />
        address<br />
        address
    </address>
    <h1 title="h1" class="elements-item">headline 1</h1>
    <h2 title="h2" class="elements-item">headline 2</h2>
    <h3 title="h3" class="elements-item">headline 3</h3>
    <h4 title="h4" class="elements-item">headline 4</h4>
    <h5 title="h5" class="elements-item">headline 5</h5>
    <h6 title="h6" class="elements-item">headline 6</h6>
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
$address: (
    background-color: transparent,
    border-color: transparent,
    border-radius: 0,
    border-style: none,
    border-width: 0,
    color: #333,
    display: block,
    font-family: sans-serif,
    font-size: 1rem,
    font-style: normal,
    font-variant-caps: normal,
    font-weight: 500,
    line-height: 1.6em,
    list-style-type: none,
    margin: 2.4rem 1rem,
    padding: 0 0 0 1rem,
    text-align: left,
    text-decoration-color: transparent,
    text-decoration-line: none,
    text-decoration-style: solid,
    text-indent: 0
);

$h1: (
    background-color: transparent,
    border-color: transparent,
    border-radius: 0,
    border-style: none,
    border-width: 0,
    color: #333,
    display: block,
    font-family: sans-serif,
    font-size: 2.4rem,
    font-style: normal,
    font-variant-caps: normal,
    font-weight: 700,
    line-height: 1em,
    list-style-type: none,
    margin: 2.4rem 1rem,
    padding: 0,
    text-align: left,
    text-decoration-color: transparent,
    text-decoration-line: none,
    text-decoration-style: solid,
    text-indent: 0
);

$h2: (
    background-color: transparent,
    border-color: transparent,
    border-radius: 0,
    border-style: none,
    border-width: 0,
    color: #333,
    display: block,
    font-family: sans-serif,
    font-size: 2.2rem,
    font-style: normal,
    font-variant-caps: normal,
    font-weight: 700,
    line-height: 1em,
    list-style-type: none,
    margin: 2.2rem 1rem,
    padding: 0,
    text-align: left,
    text-decoration-color: transparent,
    text-decoration-line: none,
    text-decoration-style: solid,
    text-indent: 0
);

$h3: (
    background-color: transparent,
    border-color: transparent,
    border-radius: 0,
    border-style: none,
    border-width: 0,
    color: #333,
    display: block,
    font-family: sans-serif,
    font-size: 2rem,
    font-style: normal,
    font-variant-caps: normal,
    font-weight: 700,
    line-height: 1em,
    list-style-type: none,
    margin: 2rem 1rem,
    padding: 0,
    text-align: left,
    text-decoration-color: transparent,
    text-decoration-line: none,
    text-decoration-style: solid,
    text-indent: 0
);

$h4: (
    background-color: transparent,
    border-color: transparent,
    border-radius: 0,
    border-style: none,
    border-width: 0,
    color: #333,
    display: block,
    font-family: sans-serif,
    font-size: 1.8rem,
    font-style: normal,
    font-variant-caps: normal,
    font-weight: 700,
    line-height: 1em,
    list-style-type: none,
    margin: 1.8rem 1rem,
    padding: 0,
    text-align: left,
    text-decoration-color: transparent,
    text-decoration-line: none,
    text-decoration-style: solid,
    text-indent: 0
);

$h5: (
    background-color: transparent,
    border-color: transparent,
    border-radius: 0,
    border-style: none,
    border-width: 0,
    color: #333,
    display: block,
    font-family: sans-serif,
    font-size: 1.8rem,
    font-style: normal,
    font-variant-caps: small-caps,
    font-weight: 700,
    line-height: 1em,
    list-style-type: none,
    margin: 1.8rem 1rem,
    padding: 0,
    text-align: left,
    text-decoration-color: transparent,
    text-decoration-line: none,
    text-decoration-style: solid,
    text-indent: 0
);

$h6: (
    background-color: transparent,
    border-color: transparent,
    border-radius: 0,
    border-style: none,
    border-width: 0,
    color: #333,
    display: block,
    font-family: sans-serif,
    font-size: 1.8rem,
    font-style: italic,
    font-variant-caps: small-caps,
    font-weight: 700,
    line-height: 1em,
    list-style-type: none,
    margin: 1.8rem 1rem,
    padding: 0,
    text-align: left,
    text-decoration-color: transparent,
    text-decoration-line: none,
    text-decoration-style: solid,
    text-indent: 0
);

:root {
    @each $property, $value in $address { #{'--address_' + $property}: $value; }
    @each $property, $value in $h1 { #{'--h1_' + $property}: $value; }
    @each $property, $value in $h2 { #{'--h2_' + $property}: $value; }
    @each $property, $value in $h3 { #{'--h3_' + $property}: $value; }
    @each $property, $value in $h4 { #{'--h4_' + $property}: $value; }
    @each $property, $value in $h5 { #{'--h5_' + $property}: $value; }
    @each $property, $value in $h6 { #{'--h6_' + $property}: $value; }
}

address { @each $property, $value in $h1 { #{$property}: var(#{'--address_' + $property}); } }
h1 { @each $property, $value in $h1 { #{$property}: var(#{'--h1_' + $property}); } }
h2 { @each $property, $value in $h2 { #{$property}: var(#{'--h2_' + $property}); } }
h3 { @each $property, $value in $h3 { #{$property}: var(#{'--h3_' + $property}); } }
h4 { @each $property, $value in $h4 { #{$property}: var(#{'--h4_' + $property}); } }
h5 { @each $property, $value in $h5 { #{$property}: var(#{'--h5_' + $property}); } }
h6 { @each $property, $value in $h6 { #{$property}: var(#{'--h6_' + $property}); } }
</style>