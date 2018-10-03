<template>
<div id="elements_content" v-on:mouseup="emitElementSelectedEvent">
    <blockquote title="blockquote" class="elements-item">blockquote</blockquote>
    <ul title="ul" class="elements-item">
        <li title="li" class="elements-item">unordered list item</li>
        <li title="li" class="elements-item">unordered list item</li>
        <li title="li" class="elements-item">unordered list item</li>
        <li title="li" class="elements-item">unordered list item</li>
    </ul>
    <ol title="ol" class="elements-item">
        <li title="li" class="elements-item">ordered list item</li>
        <li title="li" class="elements-item">ordered list item</li>
        <li title="li" class="elements-item">ordered list item</li>
        <li title="li" class="elements-item">ordered list item</li>
    </ol>
    <p title="p" class="elements-item">paragraph</p>
    <pre title="pre" class="elements-item">pre</pre>
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
$blockquote: (
    background-color: transparent,
    border-color: #000,
    border-radius: 4px,
    border-style: solid,
    border-width: 1px,
    color: #333,
    display: block,
    font-family: sans-serif,
    font-size: 1.2rem,
    font-style: italic,
    font-variant-caps: normal,
    font-weight: 500,
    line-height: 1.6em,
    list-style-type: none,
    margin: 1rem,
    padding: 1rem,
    text-align: left,
    text-decoration-color: transparent,
    text-decoration-line: none,
    text-decoration-style: solid,
    text-indent: 0
);

$ul: (
    background-color: transparent,
    border-color: transparent,
    border-radius: 0,
    border-style: none,
    border-width: 0,
    color: #333,
    display: block,
    font-family: sans-serif,
    font-size: 1.2rem,
    font-style: normal,
    font-variant-caps: normal,
    font-weight: 500,
    line-height: 1.6em,
    list-style-type: disc,
    margin: 1rem,
    padding: 0 0 0 1rem,
    text-align: left,
    text-decoration-color: transparent,
    text-decoration-line: none,
    text-decoration-style: solid,
    text-indent: 0
);

$ol: (
    background-color: transparent,
    border-color: transparent,
    border-radius: 0,
    border-style: none,
    border-width: 0,
    color: #333,
    display: block,
    font-family: sans-serif,
    font-size: 1.2rem,
    font-style: normal,
    font-variant-caps: normal,
    font-weight: 500,
    line-height: 1.6em,
    list-style-type: decimal,
    margin: 1rem,
    padding: 0 0 0 1rem,
    text-align: left,
    text-decoration-color: transparent,
    text-decoration-line: none,
    text-decoration-style: solid,
    text-indent: 0
);

$li: (
    background-color: transparent,
    border-color: transparent,
    border-radius: 0,
    border-style: none,
    border-width: 0,
    color: #333,
    display: list-item,
    font-family: sans-serif,
    font-size: 1.2rem,
    font-style: normal,
    font-variant-caps: normal,
    font-weight: 500,
    line-height: 1.6em,
    list-style-type: inherit,
    margin: 1rem,
    padding: 0,
    text-align: left,
    text-decoration-color: transparent,
    text-decoration-line: none,
    text-decoration-style: solid,
    text-indent: 0
);

$p: (
    background-color: transparent,
    border-color: transparent,
    border-radius: 0,
    border-style: none,
    border-width: 0,
    color: #333,
    display: block,
    font-family: sans-serif,
    font-size: 1.2rem,
    font-style: normal,
    font-variant-caps: normal,
    font-weight: 500,
    line-height: 1.6em,
    list-style-type: none,
    margin: 1rem,
    padding: 0,
    text-align: left,
    text-decoration-color: transparent,
    text-decoration-line: none,
    text-decoration-style: solid,
    text-indent: 0
);

$pre: (
    background-color: gainsboro,
    border-color: 1px solid gray,
    border-radius: 0,
    border-style: solid,
    border-width: 2px,
    color: #333,
    display: block,
    font-family: monospace,
    font-size: 1.2rem,
    font-style: normal,
    font-variant-caps: normal,
    font-weight: 500,
    line-height: 1.6em,
    list-style-type: none,
    margin: 1rem,
    padding: 1rem,
    text-align: left,
    text-decoration-color: transparent,
    text-decoration-line: none,
    text-decoration-style: solid,
    text-indent: 0
);

:root {
    @each $property, $value in $blockquote { #{'--blockquote_' + $property}: $value; }
    @each $property, $value in $ul { #{'--ul_' + $property}: $value; }
    @each $property, $value in $ol { #{'--ol_' + $property}: $value; }
    @each $property, $value in $li { #{'--li_' + $property}: $value; }
    @each $property, $value in $p { #{'--p_' + $property}: $value; }
    @each $property, $value in $pre { #{'--pre_' + $property}: $value; }
}

blockquote { @each $property, $value in $blockquote { #{$property}: var(#{'--blockquote_' + $property}); } }
ul { @each $property, $value in $ul { #{$property}: var(#{'--ul_' + $property}); } }
ol { @each $property, $value in $ol { #{$property}: var(#{'--ol_' + $property}); } }
li { @each $property, $value in $li { #{$property}: var(#{'--li_' + $property}); } }
p { @each $property, $value in $p { #{$property}: var(#{'--p_' + $property}); } }
pre { @each $property, $value in $pre { #{$property}: var(#{'--pre_' + $property}); } }
</style>