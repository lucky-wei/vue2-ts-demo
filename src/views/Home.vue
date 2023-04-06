<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    {{ firstName }}
    <HelloWorld
      msg="Welcome to Your Vue.js + TypeScript App"
      v-model="firstName"
    />
    <div v-for="item in userList" :key="item.id">
      年龄：{{ item.name }} 姓名：{{ item.age }} 性别：{{ item.sex }}
      <button @click="changeAge(item.id)">加年龄</button>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import HelloWorld from "@/components/HelloWorld.vue"; // @ is an alias to /src

interface IUser {
  id: number;
  name: string;
  age: number;
  sex?: number;
}

@Component({
  components: {
    HelloWorld,
  },
})
export default class Home extends Vue {
  firstName: string = "张";
  userList: Array<IUser> = [
    {
      id: 1,
      name: "张三",
      age: 18,
      sex: 0,
    },
    {
      id: 2,
      name: "黄婧",
      age: 28,
      sex: 1,
    },
  ];
  changeAge(id: number) {
    const index: IUser = this.userList.find((item) => item.id === id)!;
    index.age++;
  }

 
}
</script>
