<template>
    <td v-bind:class="classObject"
        v-bind:style="styleObject"
        v-on:click.prevent="onclick"
    >
    </td>
</template>

<script>
    export default {
        name: "Cell",
        props: {
            id: Number,
            player: Object
        },
        data: function() {
            return {
                styleObject: {
                    'background-color': null
                },
                isAvailable: true,
            };
        },
        computed: {
            classObject: function () {
                return {
                    available: this.isAvailable
                };
            }
        },
        methods: {
            onclick: function() {
                if (!this.isAvailable) {
                    return;
                }

                this.isAvailable = false;
                this.styleObject["background-color"] = this.player.color;
                this.$emit('click');
            }
        }
    }
</script>

<style scoped>
    td {
        text-align: center;
        border: thin solid #000;
        cursor: default;
        user-select: none;
    }

    .available {
        background-color: white;
    }

</style>