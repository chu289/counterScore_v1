<template>
  <div class="home_wrap">
    <div class="login" @click.prevent="send">
      <p>發送</p>
    </div>
    <p class="employeeIDTitle">員編</p>
    <input class="employeeID" type="" v-model="username" />
    <p class="passwordTitle">密碼</p>
    <input class="password" type="password" v-model="password" />
  </div>
</template>

<script>
import { ref } from "vue";
import { useRouter } from "vue-router";

export default {
  setup() {
    const username = ref("");
    const password = ref("");
    const router = useRouter();

    function send() {
      if (username.value == "admin" && password.value == "0000") {
        router.push({ path: "/" });
      } else {
        alert("帳號或密碼錯誤!");
        password.value = "";
      }
    }

    return {
      username,
      password,
      send,
    };
  },
};
</script>

<style type="text/css" src="@/assets/style.css"></style>
