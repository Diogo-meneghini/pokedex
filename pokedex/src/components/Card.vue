<script>
    export default{
        data(){
            return{
                name: '',
                id: '',
                types: [],
                img: '',
                back:{
                    bug: '#A7B723',
                    dark: '#75574C',
                    dragon: '#7037FF',
                    electric: '#F9CF30',
                    fairy: '#E69EAC',
                    fighting: '#C12239',
                    fire: '#F57D31',
                    flying: '#A891EC',
                    ghost: '#70559B',
                    normal: '#AAA67F',
                    grass: '#74CB48',
                    ground: '#DEC16B',
                    ice: '#9AD6DF',
                    poison: '#A43E9E',
                    psychic: '#FB5584',
                    rock: '#B69E31',
                    steel: '#B7B9D0',
                    water: '#6493EB'
                }
            }
        },
        props:['indice'],
        created(){
            this.getPokemons(this.indice)
        },
        watch:{
            indice:{
                handler(newValue){
                    this.getPokemons(newValue)
                }
            }
        },
        methods:{
            async getPokemons(indx){
                const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${indx}`)
                                .then(response => response.json())
                                .then(data=>{
                                    this.name = data.name
                                    this.id = data.id
                                    this.types = [...data.types]
                                    this.img = data.sprites.other['official-artwork']["front_default"]
                                })
                                .catch(error=>{
                                    console.log(error)
                                })
            },
        }
    }
</script>

<template>
    <div class="card-container">
        <div class="card">
            <span class="numero">#{{ this.id }}</span>
            <img :src="img" alt="foto poke" width="130" height="130">
            <div class="tipos">
                <ul v-for="(tipo, index) in types" :key="index">
                    <li :style="{'background-color': this.back[tipo.type.name]}">{{ tipo.type.name }}</li>
                </ul>
            </div>
            <h3 class="nome">
                {{this.name}}
            </h3>
        </div>
        
    </div>   
</template>

<style>
    card-container {
        display: flex;
    }

    .card {
        margin-right: 10px; /* Opcional: adiciona um espaço entre os elementos */
        background-color: #e6e8eb;
        border: 2px solid;
        width: 160px;
        height: 220px;
        margin: 15px 15px;
        border-radius: 10px;
        display: flex;
        align-items: center;
        flex-direction: column;
        box-shadow: 3px 3px 5px rgba(0, 0, 0, 0.6);
        
    }
    .tipos ul li{
        list-style: none;
        border: 2px solid;
        border-radius: 10px;
        width: 50px;
        justify-content: center;
        display: flex;
        margin: 5px;
        color: black;
        font-size: 1.4rem;
    }
    .card-container .card .nome{
        text-align: center;
        padding: 5px;
        font-size: 2rem;
        text-transform: capitalize;
        font-weight: 700;
    }
    .card-container .card .numero{
        align-self: flex-end;
        padding: 3px;
        font-size: 1.3rem;
        font-weight: 700;
    }
    .card-container .card .tipos{
       display: flex; 
        
    }
</style>