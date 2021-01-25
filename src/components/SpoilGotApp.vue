<template>
    <div class="hello">

        <div class="top-bar">
            <h4 class="text-left">Spoil Game of Thrones</h4>
        </div>

        <div class="container custombody" id="app">
            <div class="row column text-center">
                <select v-model="mutableSeason" @change="updateSeason"
                >
                    <option value="1">Saison 1</option>
                    <option value="2">Saison 2</option>
                    <option value="3">Saison 3</option>
                    <option value="4">Saison 4</option>
                    <option value="5">Saison 5</option>
                    <option value="6">Saison 6</option>
                    <option value="7">Saison 7</option>
                    <option value="8">Saison 8</option>

                </select>

                <!--            <h4>Saison {{ season }}</h4>-->

            </div>

            <div class="columns medium-4" v-for="(result) in mutableResult" v-bind:key="result.id">
                <div class="card">
                    <div class="card-divider">
                        <Character :perso="result"/>
                    </div>

                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import axios from 'axios'
    import Character from "./Character";

    const url = "http://localhost:8888/characters";

    export default {
        name: 'SpoilGotApp',
        components: {
             Character
        },
        props: {
            results: [],
             season: {
                type: Number,
                default: 1
            }
        },
        data: function () {
            return {
                mutableResult: this.results,
                mutableSeason: this.season
            }
        },
        methods: {

            updateSeason: function () {

                axios.get(url + "?season=" + this.mutableSeason).then(response => {
                    this.mutableResult = response.data;
                }).catch(error => {
                    alert(error.response.data.message)
                });
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    h3 {
        margin: 40px 0 0;
    }

    ul {
        list-style-type: none;
        padding: 0;
    }

    li {
        display: inline-block;
        margin: 0 10px;
    }

    a {
        color: #42b983;
    }


    .custombody{
        background : url("stark.jpg");
        background-size: initial;

    }
</style>
