<template>
    <div class="card">
        <div class="card-divider">
            <p><b v-bind:class="{ customline: deadInSeason}">{{ perso.name }}</b> {{ perso.causeOfDeath }}
            </p>
        </div>
        <!--               <div class="card-section">-->
        <!--                  <p>{{ result.causeOfDeath }}</p>-->
        <!--               </div>-->
    </div>
</template>

<script>


    export default {
        name: 'Character',
        props: {
            perso: {},
            // season: {
            //     type: Number,
            //     default: 1
            // }
        },


        data: function () {
            return {
                mutablePerso: this.perso,
                deadInSeason:this.perso.deadInSeason
            }
        }

    }
</script>

<style scoped>
    .customline {
        text-decoration: line-through;
    }
</style>
