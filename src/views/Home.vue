<template>
  <div class="home">

    <div class="m-5">
      <h1 class="text-center">Transforma sua frase em asteriscos!!</h1>
      <h3 class="text-center">(Ou o que você quiser ;P)</h3>
    </div>

    <p class="mt-5 mb-0">
      <label>Insira sua frase:</label>
      <b-form-textarea v-model="text"></b-form-textarea>
      <small class="form-text text-muted text-right">
        {{ text.length || 0 }}/267
      </small>
    </p>

    <p class="">
      <label>Trocar por:</label>
      <b-form-input v-model="replace"></b-form-input>
      <b-form-checkbox
        id="checkbox-1"
        v-model="toggle"
      >Apenas Minúsculas</b-form-checkbox>
    </p>

    <p class="mt-2">
      <label>Resultado:</label>
      <b-card class="has-shadow-1">
        <h2>{{ getAsterisk }}</h2>
      </b-card>
      <b-button variant="primary" class="mt-3">
        <b-icon icon="clipboard" font-scale="1"></b-icon> Copiar
      </b-button>
    </p>

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
