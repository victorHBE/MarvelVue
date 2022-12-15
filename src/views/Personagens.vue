<template>
<div>
    <div v-for="personagem in personagens" :key="personagem">
        {{personagem.name}}
    </div>
 
</div>
  
</template>

<script>
import axios from 'axios'
import md5 from 'md5'
export default {
    
    name: 'Personagens-pagina',
    data(){
        return {
            ts: Date.now(),
            keyPublic: 'bc99033701fd3e99c981c67793255ad9',
            keyPrivate: '8707edc7461151d35f922c510bc80c6c7ce7048b',
            personagens:[]
        }
    },
    computed: {
        hash: function(){
            return md5(this.ts+this.keyPrivate+this.keyPublic);
        }
    },
    created(){
        axios.get(`http://gateway.marvel.com/v1/public/characters?ts=${this.ts}&apikey=${this.keyPublic}&hash=${this.hash}`)
        .then(resultado => {
            console.log(resultado)
            this.personagens = resultado.data.data.results
        })
    }
}
</script>

<style>

</style>