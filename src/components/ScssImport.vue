<template>
<div>
    <input type="file" id="import" v-on:change="importScss" />
</div>
</template>

<script>
export default {
    props: ['elements', 'properties'],
    data: function () {
        return {
            
        }
    },
    methods: {
        importScss: function () {
            let file = document.getElementById('import').files[0];
            let reader = new FileReader();
            let textArray;

            reader.readAsText(file);
            reader.onload = function (e) {
                textArray = e.target.result.split(';');
                parseArray(textArray);
            };

            function parseArray (fullScssArray) {
                let filteredScssArray = fullScssArray.map((item) => {
                    let strippedItem = item.replace(/[\n\r\t]/g, '');

                    if (strippedItem.startsWith('$')) {
                        return strippedItem;
                    }

                    return false;
                });

                filteredScssArray.forEach((map) => {
                    let element = map.replace(/(\$)([a-z0-9]*)(:.*)/, '$2');
                    let properties = map.replace(/(\$.*: \()(.*)(,\))/, '$2').split(',');

                    properties.forEach((item) => {
                        let property = item.replace(/(.*)(:)(.*)/, '$1');
                        let value = item.replace(/(.*)(:)(.*)/, '$3');

                        document.documentElement.style.setProperty(`--${element}_${property}`, value)
                    });
                });
            }
        },
        importClick: function () {
            document.getElementById('import').click();
        }
    },
    created: function () {
        this.$root.$on('import_scss', () => this.importScss());
        this.$root.$on('click_import', () => this.importClick());
    }
}
</script>

<style lang="scss">
#import {
    display: none;
}
</style>