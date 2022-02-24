<template>
    <main>
        <div class="container">

            <RicercaDisco/>

            <div class="row row-cols-5">
                    <MyDisco v-for="(disco,index) in ListaDischi" 
                            :key="index"
                            :disco="disco"
                    />
            </div>
        </div>
    </main>
</template>

<script>

import MyDisco from './MyDisco.vue';
import RicercaDisco from './RicercaDisco.vue'
const axios = require('axios');

export default {
    name: 'MyMain',
    components: {
        MyDisco,
        RicercaDisco
    },
    data() {
        return {
            ListaDischi: [],
            dischiCercati: '',
            listaGeneri: []
        }
    },
    
    methods: {
        getDischi() {
            // Make a request for a user with a given ID
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then((response) => {
                // handle success
                this.ListaDischi = response.data.response;
                console.log(this.ListaDischi);
            })
            .catch(function (error) {
                // handle error
                console.log(error);
            })
            .then(function () {
                // always executed
            });
        },
        getGeneri() {
            for (let i = 0; i < this.ListaDischi.length; i++) {
                if (!this.listaGeneri.includes(this.ListaDischi[i].genre)) {
                    this.listaGeneri.push(this.ListaDischi[i].genre)
                }
            }
            return this.listaGeneri
        }
        
    },
    mounted() {
        this.getDischi();
        this.getGeneri();
    }
}
</script>

<style lang="scss" scoped>
    @import '../style/general.scss';

    main {
        background-color: #1e2d3b;
        padding-top: 30px;
    }
    .row {
        width: 80%;
        margin: auto;
        
    }
</style>