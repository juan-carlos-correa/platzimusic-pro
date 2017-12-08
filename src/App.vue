<template lang="pug">
  #app
    label(for='yearBirthday') Año de nacimiento
    input(v-model="yearBirthday" id='yearBirthday')
    p(v-if="yearBirthday") Tú edad: {{ age }}
    p Valor anterior: {{ oldVal }}
    p Valor nuevo: {{ newVal }}
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      yearBirthday: 0,
      oldVal: 0,
      newVal: 0
    }
  },

  /**
   * funciones que generan nuevas propiedades del componente en base a otras propiedades.
   * Deben ser funciones, se pueden usar como expresiones en la UI
   */
  computed: {
    age () {
      return (new Date().getFullYear()) - this.yearBirthday
    }
  },

  /**
   * Semejante al patrón Observer
   * No devuelven un valor, no son propiedades y tampoco pueden ser usadas en propiedades
   */
  watch: {
    age (newVal, oldVal) {
      console.log(newVal, oldVal)
      this.oldVal = oldVal
      this.newVal = newVal
    }
  }
}
</script>

<style lang="scss">
  @import './scss/main.scss'
</style>
