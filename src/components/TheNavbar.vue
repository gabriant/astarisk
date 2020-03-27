<template>
  <div>
    <!-- As a heading -->
    <b-navbar variant="faded" type="light">
      <b-navbar-brand  tag="h1" class="mb-0">
        <h1 id="brand">Astarisk*</h1>
      </b-navbar-brand>
        <b-navbar-nav class="ml-auto">
          <b-nav-item href="https://github.com/gabriant">
            Gabriant
            <font-awesome-icon :icon="['fab', 'github']" />
          </b-nav-item>
        </b-navbar-nav>
      </b-navbar>
  </div>
</template>

<script>
export default {
  name: 'TheNavbar'
}
</script>
