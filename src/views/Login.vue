<template>
  <h1 align = "center">업무관리 시스템</h1>
  <table align = "center">
    <tr>
        <td><label for = "id">아이디</label></td>
        <td><input type = "text" id = "id" v-model="userId" placeholder="아이디"></td>
        <td rowspan = "2"><input type ="button" class = "loginBtn" value = "로그인" @click="onLogin"></td>
    </tr>
    <tr>
        <td><label for = "password">비밀번호</label></td>
        <td><input type = "password" id = "password" v-model="userPass" placeholder="비밀번호"></td>
    </tr>
    <td colspan = "3" align = "center" class = "msg2signin">
      신규 사용자이신가요?
      <router-link to="/signup" class = "signupBtn">가입하기</router-link>
    </td>
  </table>
</template>

<script>
export default {
  data: () => ({
    userId: "",
    userPass: "",
  }),
  methods: {
    onLogin() {
          console.log({userId: this.userId, userPass: this.userPass});
          if(this.userId == "" || this.userPass == ""){
            alert("아이디와 비밀번호를 입력해주세요")
          }else{
            this.$router.replace("/project");
          }
    },
  },
};
</script>

<style scoped>
  .loginBtn {
    width: 56px;
    height: 48px;
    background-color: #e8a541;
    color: #ffffff;
    border: 3px;
    border-radius: 5px;
    font-size: 14px;
    text-align: center;
    cursor: pointer;
  }

  .msg2signin {
    font-size: 12px;
  }

  .signupBtn {
    font-size: 12px;
    color: #e8a541;
    text-align: center;
    font-weight: bold;
    cursor: pointer;
  }
</style>
