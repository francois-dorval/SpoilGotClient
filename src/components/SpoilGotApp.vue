<template>
    <div class="hello">

        <div class="top-bar">
            <h4 class="text-left">Spoil Game of Thrones</h4>
        </div>

        <div class="container" id="app">
            <div class="row column text-center">
                <!--            <input type="range" min="1" max="8" value="1" v-model="season" class="slider" style="width:80%" id="myRange">-->
                <select v-model="season" @change="updateSeason"
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

            <div class="columns medium-4" v-for="(result) in getResults()" v-bind:key="result.id">
                <div class="card">


                    <div class="card-divider">
                        <p><b v-bind:class="{ customline: result.deadInSeason}">{{ result.name }}</b> {{
                            result.causeOfDeath }}</p>
                    </div>
                    <!--               <div class="card-section">-->
                    <!--                  <p>{{ result.causeOfDeath }}</p>-->
                    <!--               </div>-->
                </div>
            </div>


        </div>
    </div>
</template>

<script>
    import axios from 'axios'

    const url = "http://localhost:8888/characters";

    export default {
        name: 'SpoilGotApp',
        props: {
            results: [],
            // season: {
            //     type: Number,
            //     default: 1
            // }
        },


        data: function () {
            return {
                mutableResult: this.results
            }
        },
        methods: {
            setResults(res){
              this.mutableResult=res;
            },
            getResults(){
                return(this.mutableResult);
            },
            updateSeason: function () {
                //this.season = value;
                //alert(JSON.stringify(this.season));
                axios.get(url + "?season=" + this.season).then(response => {
                    this.setResults(response.data);
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
</style>
