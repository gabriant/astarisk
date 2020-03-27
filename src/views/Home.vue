<template>
  <div class="home">

    <div class="m-3">
      <h1 class="text-center">Transforma sua frase em asteriscos!!</h1>
      <h3 class="text-center">(Ou no que você quiser ;P)</h3>
    </div>

    <p class="mt-2 mb-0">
      <label>Insira sua frase:</label>
      <b-form-textarea v-model="text" maxlength="267" wrap="hard"></b-form-textarea>
      <small class="form-text text-muted text-right">
        {{ text.length || 0 }}/267
      </small>
    </p>

    <p class="">
      <label>Trocar por:</label>
      <b-form-input v-model="replace" maxlength="50"></b-form-input>
      <small class="form-text text-muted text-right">
        {{ replace.length || 0 }}/50
      </small>
      <b-form-checkbox
        id="checkbox-1"
        v-model="toggle"
      >Apenas Minúsculas</b-form-checkbox>
    </p>

    <p v-if="text" class="mt-1">
      <label>Resultado:</label>
      <b-card class="result-card has-shadow-1">
        <h2>{{ getAsteriscos }}</h2>
      </b-card>

      <b-button
        variant="primary"
        class="mr-2 mt-3"
        target="_blank"
        :href="getTweet()"
      >
        <font-awesome-icon :icon="['fab', 'twitter']" /> Tweetar
      </b-button>
      <b-button variant="secondary" class="mt-3" v-clipboard:copy="getAsteriscos">
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
      replace: '*',
      hashtag: 'astarisk*',
      acentosMinus: 'àèìòùáéíóúýâêîôûãñõäëïöüÿåæœçð',
      acentosMaius: 'ÀÈÌÒÙÁÉÍÓÚÝÂÊÎÔÛÃÑÕÄËÏÖÜŸÅÆŒÇÐ'
    }
  },

  computed: {
    getAsteriscos () {
      let regex
      if (this.toggle) {
        regex = new RegExp(`[${this.acentosMinus}]|[a-z]`, 'g')
      } else {
        regex = new RegExp(`[${this.acentosMinus + this.acentosMaius}]|[A-Z]|[a-z]`, 'g')
      }
      return this.text.replace(regex, this.replace)
    }
  },

  methods: {
    getTweet () {
      return `https://twitter.com/intent/tweet?button_hashtag=${this.hashtag}&ref_src=twsrc%5Etfw&text=${this.getAsteriscos}%0A`
    }
  }
}
</script>
