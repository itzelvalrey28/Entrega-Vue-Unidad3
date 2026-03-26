<script>
export default {
  data() {
    return {
      // Requisito: Variable mensaje para interpolación
      mensaje: "Hola Mundo desde Vue"
    }
  }
}
</script>

<template>
  <main>
    <h1>{{ mensaje }}</h1>
  </main>
</template>

<style scoped>
h1 {
  text-align: center;
  margin-top: 50px;
  font-family: 'Segoe UI', sans-serif;
  color: #42b883; /* Verde característico de Vue */
}
</style>