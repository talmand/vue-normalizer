<template>
<div></div>
</template>

<script>
export default {
    props: ['elements', 'properties'],
    data: function () {
        return {
            computedStyle: window.getComputedStyle(document.body)
        }
    },
    methods: {
        exportScss: function () {
            let scss = '';
            let maps = '';
            let each = '';

            this.elements.forEach((element) => {
                maps += `$${element}: (\n`;
                this.properties.forEach((property) => {
                    maps += `\t${property}: ${this.computedStyle.getPropertyValue(`--${element}_${property}`).trim()},\n`
                });
                maps += `);\n`;

                each += `${element} {\n`;
                each += `\t@each $property, $value in $${element} { #{$property}: #{$value} }\n`;
                each += `}\n`;
            });

            scss = maps + '\n' + each;

            let blob = new Blob([scss], {type: 'text/plain;charset=utf-8'});
            let a = document.createElement('a');
            let url = URL.createObjectURL(blob);

            a.href = url;
            a.download = 'normalize.scss';
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            window.URL.revokeObjectRL(url);
        }
    },
    created: function () {
        this.$root.$on('export_scss', () => this.exportScss());
    }
}
</script>