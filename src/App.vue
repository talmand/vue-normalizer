<template>
<div id="app">
    <ScssExport v-bind:elements="elements" v-bind:properties="properties" />
    <ScssImport v-bind:elements="elements" v-bind:properties="properties" />
    <div class="grid">
        <div class="grid-boxModel">
            <BoxModel />
        </div>
        <div class="grid-examplesPanel">
            <PanelExamples />
        </div>
        <div class="grid-elements">
            <Examples />
            <div v-show="showElements">
                <ElementsSections />
                <ElementsContent />
                <ElementsInline />
            </div>
        </div>
        <div class="grid-propertiesPanel">
            <PanelProperties />
        </div>
        <div class="grid-buttonsPanel">
            <PanelButtons />
        </div>
    </div>
</div>
</template>

<script>
import BoxModel from './components/BoxModel.vue';
import ElementsSections from './components/ElementsSections.vue';
import ElementsContent from './components/ElementsContent.vue';
import ElementsInline from './components/ElementsInline.vue';
import PanelProperties from './components/PanelProperties.vue';
import PanelButtons from './components/PanelButtons.vue';
import PanelExamples from './components/PanelExamples.vue';
import Examples from './components/Examples.vue';
import ScssExport from './components/ScssExport.vue';
import ScssImport from './components/ScssImport.vue';

export default {
    name: 'app',
    data: function () {
        return {
            showBoxModelGrideElement: true,
            showExamplesGridElement: false,
            showPropertiesGridElement: true,
            showElements: true,
            elements: ['address', 'h1', 'h2', 'h3', 'h4', 'h5', 'h6', 'blockquote', 'ul', 'ol', 'li', 'p', 'pre', 'a', 'em', 'strong'],
            properties: ['background-color', 'border-color', 'border-radius', 'border-style', 'border-width', 'color', 'display', 'font-family', 'font-size', 'font-variant-caps', 'font-weight', 'line-height', 'margin', 'padding', 'text-align', 'text-decoration-color', 'text-decoration-line', 'text-decoration-style', 'text-indent']
        }
    },
    components: {
        BoxModel,
        ElementsSections,
        ElementsContent,
        ElementsInline,
        PanelProperties,
        PanelButtons,
        PanelExamples,
        Examples,
        ScssExport,
        ScssImport
    },
    methods: {
        toggleBoxModel: function () {
            let current = window.getComputedStyle(document.body).getPropertyValue('--row1').trim();
            let newValue = current === 'auto' ? 0 : 'auto';

            document.documentElement.style.setProperty('--row1', newValue);
        },
        toggleExamples: function () {
            let current = window.getComputedStyle(document.body).getPropertyValue('--col1').trim();
            let newValue = current === '0' ? '100px' : '0';

            document.documentElement.style.setProperty('--col1', newValue);
        },
        toggleProperties: function () {
            let current = window.getComputedStyle(document.body).getPropertyValue('--col3').trim();
            let newValue = current === '400px' ? '0' : '400px';

            document.documentElement.style.setProperty('--col3', newValue);
        }
    },
    created: function () {
        this.$root.$on('boxmodel_toggle', () => this.toggleBoxModel());
        this.$root.$on('examples_toggle', () => this.toggleExamples());
        this.$root.$on('properties_toggle', () => this.toggleProperties());
        this.$root.$on('show_elements', (bool) => this.showElements = bool);
    }
}
</script>

<style lang="scss">
:root {
    --col1: 0;
    --col2: 1fr;
    --col3: 400px;
    --row1: auto;
    --row2: 1fr;
    --row3: auto;
}
html {
    box-sizing: border-box;
}
*, *:before, *:after {
    box-sizing: inherit;
}

body {
	font-size: 10px;
	margin: 0;
	padding: 0;
}

#app {
    height: 100vh;
}

.grid {
    display: grid;
    grid-template-columns: var(--col1) var(--col2) var(--col3);
    grid-template-rows: var(--row1) var(--row2) var(--row3);
    grid-gap: 10px;
    height: 100%;
    padding: 10px;
    transition: 0.25s;
}
.grid-boxModel {
    border: 1px solid black;
    grid-column: 1 / 4;
    grid-row: 1;
    overflow: hidden;
}
.grid-examplesPanel {
    border: 1px solid black;
    grid-column: 1;
    grid-row: 2;
    overflow: hidden;

    button {
        padding: 0.5rem;
        width: 100%;
    }
}
.grid-elements {
    border: 1px solid black;
    grid-column: 2;
    grid-row: 2;
    overflow-y: auto;
    position: relative;

    .elements-item {
        cursor: pointer;
    }
}
.grid-propertiesPanel {
    border: 1px solid black;
    grid-column: 3;
    grid-row: 2;
    overflow: hidden;
}
.grid-buttonsPanel {
    border: 1px solid black;
    grid-column: 1 / 4;
    grid-row: 3;
    padding: 1rem;

    button {
        font-size: 1rem;
        padding: 0.5rem 1rem;
    }
}

.grid-panel-section {
    display: flex;
    flex-direction: column;
    margin: 1rem;
    padding-bottom: 1rem;

    label {
        align-items: center;
        display: flex;
        font-family: sans-serif;
        margin: 0.25rem 0;

        input,
        select {
            margin-left: auto;
            width: 50%;
        }
    }
    
    .property {
        font-size: 1rem;
        margin-right: 1rem;
    }
}
</style>
