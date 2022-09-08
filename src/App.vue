<template>
  <section>
    <img v-bind:src="picture" alt="picture" :width="size" :height="size">
    <form @submit.prevent="submitForm">
      <label for="">Enter your Nickname </label>
      <input type="text" v-on:input="setNickname">
      <button type="submit">Save</button>
    </form>

    <h1>Name : {{firstName}} {{lastName}}</h1>
    <h1>Method Name : {{getFullname()}}</h1>
    <h1>Nickname : {{nickname}}</h1>
    <h3>Age : {{age}} Years</h3>
    <p>800 + 200 = {{800 + 200}}</p>
    <p>Address : <span v-html="address"></span></p>
    <a :href="social">Facebook</a>
    <p>Hobby</p>
    <ul>
      <li>{{hobby[0]}}</li>
      <li>{{hobby[1]}}</li>
      <li>{{hobby[2]}}</li>
    </ul>
    <p>General</p>
    <ul>
      <li>Gender: {{general.gender}}</li>
      <li>Weight: {{general.weight}} cm</li>
      <li>Height: {{general.height}} kg</li>
    </ul>
    <button @click="showData">Click Me!</button>
    <button @click.ctrl="increment(10)">+10 Age</button>
    <button @click.middle="decrement">-1 Age</button>
  </section>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      firstName: "Kritsada",
      lastName: "Wiriya",
      nickname: "",
      age: 18,
      address: "<strong><i>Chiang Mai</i></strong>",
      picture: "https://www.finearts.cmu.ac.th/wp-content/uploads/2021/07/blank-profile-picture-973460_1280-1-300x300.png",
      size: 300,
      social: "https://www.facebook.com/9kritsada/",
      hobby: [
        "Play Games",
        "Learn",
        "Music"
      ],
      general: {
        gender: "Male",
        weight: "55",
        height: "180"
      }
    }
  },
  methods: {
    getFullname() {
      return `${this.firstName} ${this.lastName}`
    },
    showData() {
      alert(this.firstName)
    },
    increment(value) {
      this.age += value
    },
    decrement() {
      this.age--
    },
    setNickname(event) {
      this.nickname = event.target.value
    },
    submitForm() {
      alert("Save Nickname Complete")
    }
  }
}
</script>

<style></style>
