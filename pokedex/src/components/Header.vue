<script>
    import SearchBar from './SearchBar.vue'
    export default {
        data(){
            return{
                emited: ''
            }
        },
        emits: ['pesq', 'pesquisar'],
        components: {
            SearchBar
        },
        methods: {
            handleEmit(k){
                this.emited = k
                this.$emit('pesq', this.emited)
            }
        }
    }
</script>

<template>
    <header>
        <div class="logo">
            <img src="../assets/pokemon-logo-8.png" alt="logo img" width="200" >
        </div>
        <div class="search">
            <ion-icon name="search-outline"></ion-icon>
            <SearchBar @pesquisar="handleEmit"></SearchBar>
        </div>
    </header>
</template>

<style>
   header {
        background-color: red;
        display: flex;
        width: 100%;
        border-bottom: 2px solid;
        justify-content: space-between;
   }
   .logo{
        display: flex;
        justify-items: flex-start;
        padding: 0 5px;
   }
   .search{
        display: flex;
        justify-content: flex-end;
        align-items: center;
        padding-right: 30px;
        border: 2px; 
        /* margin: 0 auto; */
   }
   ion-icon{
        position: initial;
        color: white;
    }

   @media (max-width: 650px){
        .logo{
            width: 30%;
        }
        .logo img{
            width: 100%;
        }
   }
</style>