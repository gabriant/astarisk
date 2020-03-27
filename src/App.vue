<template>
  <div id="app">
    <b-container>
      <TheNavbar></TheNavbar>
      <b-row cols="12" class="justify-content-md-center">
        <router-view/>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import TheNavbar from './components/TheNavbar'

export default {
  components: { TheNavbar }
}
</script>
