<template>
  <section class="container">
    <div>
      <h2 class="subtitle">
        テストページ
      </h2>
      <ul class="userList">
        <li v-for="(user) in users" :key='user.id'>
          {{user.name}}
        </li>
      </ul>
    </div>
  </section>
</template>

<script lang='ts'>
import axios from 'axios'
import { Component, Vue } from 'vue-property-decorator'

@Component({
  async asyncData (context) {
    let { data } = await axios.get('https://jsonplaceholder.typicode.com/users')
    return { users: data }
  }
})
export default class Test extends Vue {
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.userList {
  text-align: left;
}
</style>
