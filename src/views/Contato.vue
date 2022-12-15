<template>
  <div id="contato">
      <h1>Pagina de contato</h1>
      <h2>{{nome}}</h2>
      <h3>{{telefone}}</h3>
      <ul>
          <li v-for="aluno in alunos" :key="aluno">{{aluno}}</li>
      </ul>
  </div>
</template>

<script>
export default {
    name: 'pagina-contato',
    data(){
        return {
            telefone: '67 98888-6795',
            nome: 'IFMS',
            alunos: ['Izabel', 'Davi', 'Victor', 'Fani']
        }
    }
}
</script>

<style scoped>
    h1{
        color: aquamarine;
    }
</style>