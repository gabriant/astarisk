<template>
  <div class="home">
    <b-container class="mt-5">
      Insira sua frase:
      <b-form-input v-model="text"></b-form-input>

      Trocar por:
      <b-form-input v-model="replace"></b-form-input>
      <b-form-checkbox
        id="checkbox-1"
        v-model="toggle"
      >Apenas Minusculas</b-form-checkbox>

      <b-card class="mt-3">
        Resultado:
        <h2>{{ getAsterisk }}</h2>

      </b-card>
    </b-container>
  </div>
</template>

<script>

export default {
  name: 'Home',

  data() {
    return {
      text: '',
      toggle: false,
      replace: '*'
    }
  },

  computed: {
    getAsterisk () {
      let result
      if (this.toggle) {
        result = this.text.replace(/([a-z])/g, this.replace)
      } else {
        result = this.text.replace(/([A-Z]|[a-z])/g, this.replace)
      }
      return result
    }
  }
}
</script>
