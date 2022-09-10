<template>
  <section>
    <img v-bind:src="picture" alt="picture" :width="size" :height="size" ref="imageEl">
    <form @submit.prevent="submitForm">
      <label for="">Enter your Nickname </label>
      <!-- <input type="text" v-on:input="setNickname" ref="nickNameEl"> -->
      <input type="text" ref="nickNameEl">
      <button type="submit">Save</button>
    </form>
    <h1>Name : {{ getFullname }}</h1>
    <h1 v-if="nickname.length === 0">ไม่ทราบ Nickname</h1>
    <div v-else>
      <h1>Nickname : {{nickname}}</h1>
    </div>
    <h1>เงินเดือน {{ salary }} บาท</h1>
    <h1>รายได้ต่อปี {{ getIncome }}</h1>
    <h3>ตำแหน่งงาน : {{ getDepartment }}</h3>
    <button @click="addSalary(5000)">เพิ่มเงินเดือน</button>
    <br><br>
    <button @click="toggleVisible">{{ isVisible ? "ซ่อน" : "แสดง"}} รายละเอียด</button>
    <article v-show="isVisible">
      <h3>Age : {{ age }} Years</h3>
      <p>800 + 200 = {{800 + 200}}</p>
      <p>Address : <span v-html="address"></span></p>
      <a :href="social">Facebook</a>
      <p>Hobby</p>
      <ul>
        <li v-for="(item, index) in hobby" :key="index">{{index + 1}}. {{item}}</li>
      </ul>
      <p>General</p>
      <ul>
        <!-- <li>Gender: {{general.gender}}</li>
      <li>Weight: {{general.weight}} cm</li>
      <li>Height: {{general.height}} kg</li> -->
        <li v-for="(item, key) in general" :key="key">{{key}} {{item}}</li>
      </ul>
      <button @click="showData">Click Me!</button>
      <button @click.ctrl="increment(10)">+10 Age</button>
      <button @click.middle="decrement">-1 Age</button>
      <hr>
      <h2>Method: {{ getRandomByMethod() }}</h2>
      <h2>Method: {{ getRandomByMethod() }}</h2>
      <hr>
      <h2>Computed: {{ getRandomByComputed }}</h2>
      <h2>Computed: {{ getRandomByComputed }}</h2>
    </article>
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
      },
      salary: 25000,
      isVisible: false
    }
  },
  methods: {
    showData() {
      alert(this.firstName)
    },
    increment(value) {
      this.age += value
    },
    decrement() {
      this.age--
    },
    // setNickname(event) {
    //   this.nickname = event.target.value
    // },
    submitForm() {
      // e.preventDefault();
      // console.log(this.$refs.nickNameEl)
      // alert("Set Nickname Complete")
      this.nickname = this.$refs.nickNameEl.value
    },
    toggleVisible() {
      this.isVisible = !this.isVisible
    },
    getRandomByMethod() {
      return Math.random()
    },
    addSalary(value) {
      this.salary += value
    }
  },
  computed: {
    getFullname() {
      return `${this.firstName} ${this.lastName}`
    },
    getRandomByComputed() {
      return Math.random()
    },
    getIncome() {
      return this.salary * 12
    },
    getDepartment() {
      return this.salary >= 35000 ? "Project menager" : "Programer"
    }
  },
  watch: {
    salary(value) {
      if(value > 50000) {
        alert("เงินเดือนไม่ควรเกิน 50,000 บาท")
        setTimeout(() => {
          this.salary = 50000
        }, 100)
      }
    }
  }
}
</script>

<style>

</style>
