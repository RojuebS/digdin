<template>
  <div class="container">
    <h1>{{ titulo }}</h1>
    <ul>
      <li v-for="foto of fotos">
        <meu-painel :titulo="foto.titulo">
            <img class="responsiva" :src="foto.url" :alt="foto.titulo">
        </meu-painel>
      </li>
    </ul>
  </div>
</template>

<script>
  import Painel from './components/shared/painel/Painel';
export default {

  components: {
    'meu-painel': Painel
  },

  data () {
    return {
      titulo: 'Alurapic',
      fotos: []
    }
  },
  created() {
    this.$http.get('http://localhost:3000/v1/fotos')
      .then(res => res.json())
      .then(fotos => this.fotos = fotos, err => console.log(err))
  }
}
</script>

<style>

  .container {
    width: 96%;
    margin: 0 auto;
    font-family: Helvetica;
  }
  h1 {
    text-align: center;
  }

  li { list-style: none; }

  li { display: inline-block;}

</style>
