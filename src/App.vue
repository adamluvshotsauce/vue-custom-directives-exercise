<template>
    <div class="container">
        <div class="row">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <h1>Directives Exercise</h1>
                <!-- Exercise -->
                <!-- Build a Custom Directive which works like v-on (Listen for Events) -->
                <button class="btn btn-primary" v-customOn:click="pressed">Try Me!</button>
                <hr>
                <div style="width: 100px; height: 100px; background-color: lightblue"
                     v-customOn:mouseenter="mouseEntered"
                     v-customOn:mouseleave="mouseLeave"></div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        directives: {
            'customOn': {
                bind(el, binding, vnode) {
                    // el.onclick = function() {
                    //     binding.value();
                    // }
                    const type = binding.arg;
                    const ftn = binding.value;
                    el.addEventListener(type, ftn);
                }
            }
        },
        methods: {
            pressed() {
                alert('Nice try!');

            },
            mouseEntered() {
                console.log('Mouse entered!');
            },
            mouseLeave() {
                console.log('Mouse left!');
            }
        }
    }
</script>

<style>
</style>
