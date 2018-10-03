<template>
<div id="boxmodel">
    <div class="boxmodel-margin" v-bind:style="{padding: el_margin}">
        <div class="boxmodel-border" v-bind:style="{padding: el_border}">
            <div class="boxmodel-padding" v-bind:style="{padding: el_padding}">
                <div class="boxmodel-element" v-html="html"></div>
            </div>
        </div>
    </div>
</div>
</template>

<script>
export default {
    data: function () {
        return {
            html: '',
            el: null,
            el_margin: null,
            el_border: null,
            el_padding: null
        }
    },
    methods: {
        updateBoxModel: function (element) {
            this.html = element.outerHTML;
            this.el_margin = window.getComputedStyle(document.documentElement).getPropertyValue('--' + element.tagName.toLowerCase() + '_margin');
			this.el_border = window.getComputedStyle(document.documentElement).getPropertyValue('--' + element.tagName.toLowerCase() + '_border-width');
            this.el_padding = window.getComputedStyle(document.documentElement).getPropertyValue('--' + element.tagName.toLowerCase() + '_padding');
        }
    },
    created: function () {
        this.$root.$on('element_selected', e => this.updateBoxModel(e));
        this.$root.$on('update_boxmodel_margin', margin => this.el_margin = margin);
        this.$root.$on('update_boxmodel_border', border => this.el_border = border);
        this.$root.$on('update_boxmodel_padding', padding => this.el_padding = padding);
    }
}
</script>

<style>
.boxmodel-margin {
	background-color: #ffff9f;
	transition: 0.25s;
}
.boxmodel-border {
	background-color: #513f3f;
	transition: 0.25s;
}
.boxmodel-padding {
	background-color: #9f779f;
	transition: 0.25s;
}
.boxmodel-element {
	background-color: #b6b6ff;
	transition: 0.25s;
}
.boxmodel-element > * {
    background-color: transparent !important;
    border: none !important;
    list-style-type: none !important;
    margin: 0 !important;
    padding: 0 !important;
}
</style>