<template>
<section id="panel_properties" class="grid-panel-section">
    <div class="current-element">{{ currentElement }}</div>
    <label class="background-color">
        <span class="property">background-color: </span>
        <input type="text" v-model="backgroundColor" />
    </label>
    <label class="border-color">
        <span class="property">border-color: </span>
        <input type="text" v-model="borderColor" />
    </label>
    <label class="border-radius">
        <span class="property">border-radius: </span>
        <input type="text" v-model="borderRadius" />
    </label>
    <label class="border-style">
        <span class="property">border-style: </span>
        <select v-model="borderStyle">
            <option v-for="(option, key) in borderStyleOptions" v-bind:value="option" v-bind:key="key">{{ option }}</option>
        </select>
    </label>
    <label class="border-width">
        <span class="property">border-width: </span>
        <input type="text" v-model="borderWidth" />
    </label>
    <label class="color">
        <span class="property">color: </span>
        <input type="text" v-model="color" />
    </label>
    <label class="display">
        <span class="property">display: </span>
        <select v-model="display">
            <option v-for="(option, key) in displayOptions" v-bind:value="option" v-bind:key="key">{{ option }}</option>
        </select>
    </label>
    <label class="font-family">
        <span class="property">font-family: </span>
        <input type="text" v-model="fontFamily" />
    </label>
    <label class="font-size">
        <span class="property">font-size: </span>
        <input type="text" v-model="fontSize" />
    </label>
    <label class="font-style">
        <span class="property">font-style: </span>
        <select v-model="fontStyle">
            <option v-for="(option, key) in fontStyleOptions" v-bind:value="option" v-bind:key="key">{{ option }}</option>
        </select>
    </label>
    <label class="font-variant-caps">
        <span class="property">font-variant-caps: </span>
        <select v-model="fontVariantCaps">
            <option v-for="(option, key) in fontVariantCapsOptions" v-bind:value="option" v-bind:key="key">{{ option }}</option>
        </select>
    </label>
    <label class="font-weight">
        <span class="property">font-weight: </span>
        <input type="text" v-model="fontWeight" />
    </label>
    <label class="line-height">
        <span class="property">line-height: </span>
        <input type="text" v-model="lineHeight" />
    </label>
    <label class="list-style-type">
        <span class="property">list-style-type: </span>
        <select v-model="listStyleType">
            <option v-for="(option, key) in listStyleTypeOptions" v-bind:value="option" v-bind:key="key">{{ option }}</option>
        </select>
    </label>
    <label class="border-color">
        <span class="property">margin: </span>
        <input type="text" v-model="margin" />
    </label>
    <label class="border-radius">
        <span class="property">padding: </span>
        <input type="text" v-model="padding" />
    </label>
    <label class="text-align">
        <span class="property">text-align: </span>
        <select v-model="textAlign">
            <option v-for="(option, key) in textAlignOptions" v-bind:value="option" v-bind:key="key">{{ option }}</option>
        </select>
    </label>
    <label class="text-decoration-color">
        <span class="property">text-decoration-color: </span>
        <input type="text" v-model="textDecorationColor" />
    </label>
    <label class="text-decoration-line">
        <span class="property">text-decoration-line: </span>
        <select v-model="textDecorationLine">
            <option v-for="(option, key) in textDecorationLineOptions" v-bind:value="option" v-bind:key="key">{{ option }}</option>
        </select>
    </label>
    <label class="text-decoration-style">
        <span class="property">text-decoration-style: </span>
        <select v-model="textDecorationStyle">
            <option v-for="(option, key) in textDecorationStyleOptions" v-bind:value="option" v-bind:key="key">{{ option }}</option>
        </select>
    </label>
    <label class="text-indent">
        <span class="property">text-indent: </span>
        <input type="text" v-model="textIndent" />
    </label>
</section>
</template>

<script>
export default {
    data: function () {
        return {
            backgroundColor: null,
            currentElement: 'select an element',
            borderColor: null,
            borderRadius: null,
            borderStyle: null,
            borderWidth: null,
            color: null,
            display: null,
            fontFamily: null,
            fontSize: null,
            fontStyle: null,
            fontVariantCaps: null,
            fontWeight: null,
            lineHeight: null,
            listStyleType: null,
            margin: null,
            padding: null,
            textAlign: null,
            textDecorationColor: null,
            textDecorationLine: null,
            textDecorationStyle: null,
            textIndent: null,
            fontStyleOptions: ['normal', 'italic', 'oblique'],
            fontVariantCapsOptions: ['all-petite-caps', 'all-small-caps', 'normal', 'petite-caps', 'small-caps', 'titling-caps', 'uncase'],
            listStyleTypeOptions: ['disc', 'circle', 'square', 'decimal', 'georgian', 'none', 'inherit'],
            textAlignOptions: ['center', 'end', 'justify-all', 'justify', 'left', 'match-parent', 'right', 'start'],
            textDecorationLineOptions: ['line-through', 'none', 'overline', 'underline'],
            textDecorationStyleOptions: ['dashed', 'dotted', 'double', 'solid', 'wavy'],
            borderStyleOptions: ['dashed', 'dotted', 'double', 'groove', 'hidden', 'inset', 'none', 'outset', 'ridge', 'solid'],
            displayOptions: ['block', 'flex', 'grid', 'inline-block', 'inline', 'list-item', 'none']
        }
    },
    methods: {
        createPanel: function (element) {
            this.currentElement = element.tagName.toLowerCase();
            this.backgroundColor = window.getComputedStyle(document.body).getPropertyValue(`--${this.currentElement}_background-color`).trim();
            this.borderColor = window.getComputedStyle(document.body).getPropertyValue(`--${this.currentElement}_border-color`).trim();
            this.borderRadius = window.getComputedStyle(document.body).getPropertyValue(`--${this.currentElement}_border-radius`).trim();
            this.borderStyle = window.getComputedStyle(document.body).getPropertyValue(`--${this.currentElement}_border-style`).trim();
            this.borderWidth = window.getComputedStyle(document.body).getPropertyValue(`--${this.currentElement}_border-width`).trim();
            this.color = window.getComputedStyle(document.body).getPropertyValue(`--${this.currentElement}_color`).trim();
            this.display = window.getComputedStyle(document.body).getPropertyValue(`--${this.currentElement}_display`).trim();
            this.fontFamily = window.getComputedStyle(document.body).getPropertyValue(`--${this.currentElement}_font-family`).trim();
            this.fontSize = window.getComputedStyle(document.body).getPropertyValue(`--${this.currentElement}_font-size`).trim();
            this.fontStyle = window.getComputedStyle(document.body).getPropertyValue(`--${this.currentElement}_font-style`).trim();
            this.fontVariantCaps = window.getComputedStyle(document.body).getPropertyValue(`--${this.currentElement}_font-variant-caps`).trim();
            this.fontWeight = window.getComputedStyle(document.body).getPropertyValue(`--${this.currentElement}_font-weight`).trim();
            this.lineHeight = window.getComputedStyle(document.body).getPropertyValue(`--${this.currentElement}_line-height`).trim();
            this.listStyleType = window.getComputedStyle(document.body).getPropertyValue(`--${this.currentElement}_list-style-type`).trim();
            this.margin = window.getComputedStyle(document.body).getPropertyValue(`--${this.currentElement}_margin`).trim();
            this.padding = window.getComputedStyle(document.body).getPropertyValue(`--${this.currentElement}_padding`).trim();
            this.textAlign = window.getComputedStyle(document.body).getPropertyValue(`--${this.currentElement}_text-align`).trim();
            this.textDecorationColor = window.getComputedStyle(document.body).getPropertyValue(`--${this.currentElement}_text-decoration-color`).trim();
            this.textDecorationLine = window.getComputedStyle(document.body).getPropertyValue(`--${this.currentElement}_text-decoration-line`).trim();
            this.textDecorationStyle = window.getComputedStyle(document.body).getPropertyValue(`--${this.currentElement}_text-decoration-style`).trim();
            this.textIndent = window.getComputedStyle(document.body).getPropertyValue(`--${this.currentElement}_text-indent`).trim();
        }
    },
    created: function () {
        this.$root.$on('element_selected', element => this.createPanel(element));
    },
    watch: {
        backgroundColor: function (value) {
            document.documentElement.style.setProperty(`--${this.currentElement}_background-color`, value);
        },
        borderColor: function (value) {
            document.documentElement.style.setProperty(`--${this.currentElement}_border-color`, value);
        },
        borderRadius: function (value) {
            document.documentElement.style.setProperty(`--${this.currentElement}_border-radius`, value);
        },
        borderStyle: function (value) {
            document.documentElement.style.setProperty(`--${this.currentElement}_border-style`, value);
        },
        borderWidth: function (value) {
            document.documentElement.style.setProperty(`--${this.currentElement}_border-width`, value);
            this.$root.$emit('update_boxmodel_border', value);
        },
        color: function (value) {
            document.documentElement.style.setProperty(`--${this.currentElement}_color`, value);
        },
        display: function (value) {
            document.documentElement.style.setProperty(`--${this.currentElement}_display`, value);
        },
        fontFamily: function (value) {
            document.documentElement.style.setProperty(`--${this.currentElement}_font-family`, value);
        },
        fontSize: function (value) {
            document.documentElement.style.setProperty(`--${this.currentElement}_font-size`, value);
        },
        fontStyle: function (value) {
            document.documentElement.style.setProperty(`--${this.currentElement}_font-style`, value);
        },
        fontVariantCaps: function (value) {
            document.documentElement.style.setProperty(`--${this.currentElement}_font-variant-caps`, value);
        },
        fontWeight: function (value) {
            document.documentElement.style.setProperty(`--${this.currentElement}_font-weight`, value);
        },
        margin: function (value) {
            document.documentElement.style.setProperty(`--${this.currentElement}_margin`, value);
            this.$root.$emit('update_boxmodel_margin', value);
        },
        padding: function (value) {
            document.documentElement.style.setProperty(`--${this.currentElement}_padding`, value);
            this.$root.$emit('update_boxmodel_padding', value);
        },
        lineHeight: function (value) {
            document.documentElement.style.setProperty(`--${this.currentElement}_line-height`, value);
        },
        listStyleType: function (value) {
            document.documentElement.style.setProperty(`--${this.currentElement}_list-style-type`, value);
        },
        textAlign: function (value) {
            document.documentElement.style.setProperty(`--${this.currentElement}_text-align`, value);
        },
        textDecorationColor: function (value) {
            document.documentElement.style.setProperty(`--${this.currentElement}_text-decoration-color`, value);
        },
        textDecorationLine: function (value) {
            document.documentElement.style.setProperty(`--${this.currentElement}_text-decoration-line`, value);
        },
        textDecorationStyle: function (value) {
            document.documentElement.style.setProperty(`--${this.currentElement}_text-decoration-style`, value);
        },
        textIndent: function (value) {
            document.documentElement.style.setProperty(`--${this.currentElement}_text-indent`, value);
        }
    }
}
</script>

<style lang="scss">
.current-element {
    border-bottom: 1px solid gainsboro;
    font-family: sans-serif;
    font-size: 1rem;
    font-weight: bold;
    margin: 0 0 1rem;
    padding: 0 0 1rem 0;
    text-align: center;
}
</style>