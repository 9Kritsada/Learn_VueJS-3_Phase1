<template>
  <section>
    <h1>Firstname : {{firstName}}</h1>
    <h1>Lastname : {{firstName}}</h1>
    <h3>Age : {{age}} Years</h3>
    <p>800 + 200 = {{800 + 200}}</p>
    <p>Address : <span v-html="address"></span></p>
  </section>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      firstName : "Kritsada",
      lastName : "Wiriya",
      age: 18,
      address: "<strong><i>Chiang Mai</i></strong>"
    }
  }
}
</script>

<style></style>
