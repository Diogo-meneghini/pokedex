<script>
    export default{
        data(){
            return{
                pesquisa: '',
            }
        },
        emits: ['pesquisar'],
        methods: {
                    handlePesquisa(){
                        this.$emit('pesquisar', this.pesquisa);
                        this.pesquisa = ''
                    }
                }
    }
</script>

<template>
    <div class="container">
        <div class="search-container">
            <form @submit.prevent="handlePesquisa">
                <input v-model="pesquisa" type="text" placeholder="Digite o nome do pokemon">
            </form>
        </div>
    </div>
</template>

<style scoped>
    .container{
        display: flex;
        align-items: center;
        justify-content: center;
        /* padding: 20px;  */
    }
    .search-container input[type=text] {
        display: flex;
        align-items: center;
        padding: 10px;
        width: 200px;
        border: none;
        border-radius: 25px;
        font-size: 16px;
        height: 20px;
    }
    .search-container ::placeholder{
        font-size: 1.5rem;
    }
    
    @media (max-width: 650px){
        .search-container input[type=text]{
            width: 100%;
            justify-content: space-between;
        }
    }
</style>