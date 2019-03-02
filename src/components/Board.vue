<template>
    <table class="gameboard">
        <tr v-for="row in rows"
            :key="row.id"
        >
            <td is="Cell"
                v-for="cell in row.cells"
                v-bind="cell"
                v-bind:player="player"
                v-on:click="onclick"
                :key="cell.id"
            ></td>
        </tr>
    </table>
</template>

<script>
    import Cell from './Cell'

    export default {
        name: "Board",
        components: {
            Cell
        },
        props: {
            size: Number
        },
        computed: {
            rows: function () {
                var ret = [];

                for(var row = 0; row < this.size; row++) {
                    var cells = [];

                    for (var cell = 0; cell < this.size; cell++) {
                        cells.push({
                            id: row * this.size + cell
                        });
                    }

                    ret.push({
                        id: row,
                        cells: cells
                    });
                }

                return ret;
            },
            player: function () {
                var id = Math.floor(Math.random() * 10);

                var colors = [
                    'teal',
                    'aquamarine',
                    'aqua',
                    'antiquewhite',
                    'red',
                    'deepskyblue',
                    'dodgerblue',
                    'darkviolet',
                    'fuchsia',
                    'hotpink',
                    'tan',
                    'tomato'
                ];

                return {
                    id: id,
                    color: colors[id]
                }
            }
        },
        methods: {
            onclick: function () {
            }
        }
    }
</script>

<style scoped>
    table {
        margin: 0 auto;
        border-collapse: collapse;
    }

    tr {
        height: 50px;
    }

    td {
        width: 50px;
    }
</style>