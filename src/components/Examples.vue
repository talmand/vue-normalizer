<template>
<div id="examples">
    <div v-show="showLoremIpsum">
        <h1>Lorem Ipsum</h1>

        <h2>Headline 2</h2>
        <p>Lorem ipsum dolor sit amet, <a href="#">consectetur adipiscing</a> elit. Sed auctor placerat sem id aliquam. Quisque auctor, augue vel rutrum mattis, odio nisl consequat nisi, ac vehicula leo sem semper sem. Mauris venenatis aliquet urna at facilisis. Praesent lacus arcu, cursus eget blandit vitae, pellentesque vitae erat. Etiam sit amet mattis diam. Donec non tincidunt est. Etiam at cursus urna. Ut mollis mi nibh, eget semper mi posuere vitae. Ut vulputate semper interdum. Pellentesque laoreet venenatis mi, quis elementum dolor interdum sit amet. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Cras rutrum, ligula ultrices tristique dapibus, massa tortor dictum neque, eu euismod est velit quis nulla.</p>
        <p>Donec bibendum tortor <em>quis ante consectetur</em> condimentum. Etiam vehicula turpis lorem, a tincidunt libero convallis sed. Proin pulvinar imperdiet risus, vitae lacinia nulla semper vitae. Etiam vel enim dictum, rutrum ligula sed, aliquet nunc. Mauris eu erat dictum, placerat tortor non, viverra nisi. Aenean at bibendum ex, in viverra eros. Maecenas nec enim ut magna auctor feugiat at vel lacus. Ut dui lectus, imperdiet et ipsum at, varius euismod tortor. Sed leo lorem, aliquam eu vestibulum sit amet, tempus vitae augue. Suspendisse potenti. Sed consequat risus eget quam iaculis, quis lobortis sem lobortis. Donec non fermentum urna. Suspendisse ut velit quis tellus congue venenatis. Cras imperdiet, nibh non varius semper, odio massa ullamcorper neque, at consequat purus nunc in risus. Pellentesque id elit vitae dui blandit tristique nec ac ex. Aenean non pretium turpis.</p>

        <h3>Headline 3</h3>
        <p>Fusce elit urna, ultricies sed neque ut, <a href="#">luctus convallis</a> massa. Pellentesque eu posuere massa, id tincidunt sem. Nunc cursus eu lectus lobortis suscipit. Maecenas id quam nibh. In nunc erat, mollis vel accumsan vitae, egestas ac mi. Fusce a mi vitae massa imperdiet hendrerit sit amet eget mauris. Donec pulvinar, mauris id posuere convallis, ante lacus rutrum eros, vitae fringilla ipsum massa vel neque. Donec turpis dolor, placerat vitae ligula ut, porta ullamcorper erat. Aenean quis magna tortor. Curabitur malesuada placerat ligula mattis fringilla. Cras ultrices erat libero, nec faucibus nibh gravida nec. Nulla facilisi. Pellentesque semper mattis interdum. Curabitur pellentesque vestibulum justo, nec viverra nisi rhoncus eget.</p>
        <p>Cras bibendum lobortis libero, <em>condimentum posuere nulla</em> tempor ac. Ut tristique nunc ante, vel dictum augue accumsan a. Phasellus eget nibh sollicitudin, maximus ex sed, scelerisque velit. Etiam et felis et sapien lobortis vulputate. Duis rutrum sollicitudin tellus, eu interdum massa pretium a. Etiam tincidunt suscipit nisl, ut imperdiet diam iaculis in. Nulla tristique a ante at scelerisque.</p>

        <h4>Headline 4</h4>
        <p>Proin suscipit, nulla sed euismod finibus, ligula sem volutpat urna, nec bibendum enim enim euismod eros. Donec congue, ex non euismod consequat, ligula nulla ultrices orci, in molestie felis ex eu tellus. Sed dictum, quam laoreet accumsan bibendum, diam turpis dignissim ipsum, sed mattis eros enim ut justo. Integer eleifend gravida tellus in blandit. Nullam quis massa nisl. Phasellus leo ligula, malesuada in dignissim non, fermentum ut purus. Nunc porttitor egestas consequat. Aenean molestie ut lacus eu mattis. Cras nec lectus urna. Nulla eleifend neque ut urna egestas, quis auctor purus fringilla. Donec nec ligula placerat, dignissim diam quis, ultricies lectus. Sed sed nulla et arcu eleifend suscipit sit amet eu nunc. Nunc in consectetur diam. Fusce pharetra accumsan laoreet. Nulla sollicitudin luctus vulputate. Ut elementum lacus vitae lectus finibus, in dapibus felis elementum.</p>
    </div>
    <div v-show="showLists">
        <p>This is an example of an address:</p>
        <address>
            <span>Tyler Durden</span><br />
            <span>1537 Paper Street</span><br />
            <span>Bradford DE 19808</span>
        </address>

        <p>This is an example of an unordered list:</p>
        <ul>
            <li>5 egg yolks, beaten</li>
            <li>1 (14 ounce) can sweetened condensed milk</li>
            <li>1/2 cup key lime juice</li>
            <li>1 (9 inch) prepared graham cracker crust</li>
        </ul>

        <p>This is an example of an ordered list:</p>
        <ol>
            <li>Preheat oven to 375 degrees F (190 degrees C).</li>
            <li>Combine the egg yolks, sweetened condensed milk and lime juice. Mix well. Pour into unbaked graham cracker shell.</li>
            <li>Bake in preheated oven for 15 minutes. Allow to cool. Top with whipped topping and garnish with lime slices if desired.</li>
        </ol>
    </div>
</div>
</template>

<script>
export default {
    data: function () {
        return {
            showLoremIpsum: false,
            showLists: false
        }
    },
    methods: {
        exampleLoremIpsum: function () {
            this.showLoremIpsum = !this.showLoremIpsum;
            this.$root.$emit('show_elements', !this.showLoremIpsum);
        },
        exampleLists: function () {
            this.showLists = !this.showLists;
            this.$root.$emit('show_elements', !this.showLists);
        }
    },
    created: function () {
        this.$root.$on('example_loremipsum', () => this.exampleLoremIpsum());
        this.$root.$on('example_lists', () => this.exampleLists());
    }
}
</script>

<style lang="scss">
#examples {
    background: white;
    left: 0;
    position: absolute;
    top: 0;
    width: 100%;
    z-index: 100;
}
</style>