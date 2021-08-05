<template>
  <div>
    <h1>Monitoramento PJE</h1>
      <v-data-table
        :headers="headers"
        :items="lista"
        :items-per-page="10"
        class="elevation-1"
      ></v-data-table>

  </div>
</template>

<script>

export default {

  data () {
    return {
      lista: [],
      headers: [
          { text: 'Titulo', value: 'dsTitulo' },
        ],
      }
  },
  mounted () {
    this.carregar()
  },
  methods: {
    carregar (params) {
      this.$axios.get('https://pjeportal-desenv.apps.tjdft.jus.br/monitoramento/consulta').then(response => {
        this.lista = response.data.results
      })
    },
  }
}
</script>