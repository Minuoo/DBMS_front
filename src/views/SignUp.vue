<template>
  <h1 align = "center">회원가입</h1>
        <table align = "center">
            <tr>
                <td><label for = "name">이름</label></td>
                <td><input type = "text" v-model="name" placeholder="이름"></td>
            </tr>
            <tr>
                <td><label for = "id">아이디</label></td>
                <td><input type = "text" v-model="userId" id = "id" placeholder="아이디"></td>
            </tr>
            <tr>
                <td><label for = "password">비밀번호</label></td>
                <td><input type = "password" v-model="userPass" id = "password"  placeholder="비밀번호"></td>
            </tr>
            <tr>
                <td><label for = "confirm">비밀번호 확인</label></td>
                <td><input type = "password" v-model="userPassConfirmed" id = "confirm" placeholder="비밀번호 확인"></td>
            </tr>
            <tr class="text-info" v-if="userPass != userPassConfirmed" rowspan = "2" align = "center">일치하지 않습니다</tr>
            <tr>
                <td><label for = "spec">최종학력</label></td>
                <td><input type = "text" v-model="spec" id = "spec"  placeholder="최종학력"></td>
            </tr>
            <tr>
                <td colspan = "2" align = "center">
                	<input type ="button" class = "signupBtn" value = "회원가입" @click="signUp">
                  <input type ="button" class = "backBtn" value = "로그인" @click="back">
                </td>
            </tr>
        </table>

</template>

<script>
export default {
  data: () => ({
    name: "",
    userId: "",
    userPass: "",
    userPassConfirmed: "",
    spec: ""
  }),
  methods: {
    signUp() {
      console.log({name: this.name, ID: this.userId, PW: this.userPass, spec: this.spec});
      alert("회원가입이 완료되었습니다.");
    },
    back() {
      this.$router.replace("/");
    },
  },
};
</script>

<style scoped>
  .signupBtn {
    width: 72px;
    height: 32px;
    background-color: #e8a541;
    color: #ffffff;
    border: 3px;
    border-radius: 5px;
    font-size: 14px;
    text-align: center;
    cursor: pointer;
    margin-left: 15px;
  }
  .backBtn {
    width: 72px;
    height: 32px;
    background-color: #e8a541;
    color: #ffffff;
    border: 3px;
    border-radius: 5px;
    font-size: 14px;
    text-align: center;
    cursor: pointer;
    margin-left: 15px;
  }
  .text-info {
    color: #e84141;
    font-size: 12px;
    text-align: center;
  }
</style>
