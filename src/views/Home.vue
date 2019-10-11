<template>
  <div class="home">
    <form action>
      <input type="text" v-model="usuario.nome"/>
      <input type="password" v-model="usuario.pass"/>
      <button type="submit" @click.prevent="submit"> submit </button>
      <button type="submit" @click.prevent="submitAgain"> teste </button>
    </form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data(){
    return {
      usuario: {}
    }
  },
  methods: {
    submit(){
      axios.post('http://localhost:8080/mercado/login', this.usuario, {withCredentials: true})
        .then(res => console.log('sucesso', res.data))
        .catch(e => console.error(e));
    },
    submitAgain(){
      axios.get('http://localhost:8080/mercado/login/teste',{withCredentials: true})
        .then(res => console.log('sucesso', res.data))
        .catch(e => console.error(e));
    },
  }
};
</script>
