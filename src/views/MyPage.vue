<template>
<nav>
    <router-link to="/project" class = "nav-menu">프로젝트</router-link>
    <router-link to="/employee" class = "nav-menu">직원</router-link>
    <router-link to="/devinfo" class = "nav-menu">경력관리</router-link>
    <router-link to="/mypage" class = "nav-menu">MY</router-link>
    <router-link to="/" class = "nav-menu">로그아웃</router-link>
</nav>
  <h1 align = "center">마이페이지</h1>
        <table align = "center">
            <tr>
                <td><label for = "name">사번</label></td>
                <td> {{myData.code}}</td>
            </tr>
            <tr>
                <td><label for = "name">이름</label></td>
                <td>{{myData.name}}</td>
            </tr>
            <tr>
                <td><label for = "id">아이디</label></td>
                <td>{{myData.ID}}</td>
            </tr>
            <br>
            <tr>
                <td><label for = "password">현재 비밀번호</label></td>
                <td><input type = "password" v-model="userPass" id = "password"></td>
            </tr>
            <tr class="text-info" v-if="userPass != myData.PW" rowspan = "2" align = "center">비밀번호를 다시 확인해주세요</tr>
            <tr>
                <td><label for = "password">새 비밀번호</label></td>
                <td><input type = "password" v-model="userNewPass" id = "newPass"></td>
            </tr>
            <tr>
                <td><label for = "password">새 비밀번호 확인</label></td>
                <td><input type = "password" v-model="userNewPassConfirmed" id = "newPassConfirmed"></td>
            </tr>
            <tr class="text-info" v-if="userNewPass != userNewPassConfirmed" rowspan = "2" align = "center">일치하지 않습니다</tr>
            <br>
            <tr>
                <td><label for = "spec">최종학력</label></td>
                <td><input type = "text" v-model="myData.spec" id = "spec"></td>
            </tr>
            <tr>
                <td colspan = "2" align = "center">
                	<input type ="button" class = "signupBtn" value = "수정" @click="onEdit">
                </td>
            </tr>
        </table>

</template>

<script>
export default {
  data: () => ({
      userPass: "",
      userNewPass: "",
      userNewPassConfirmed: "",
      spec: "",
      myData: {
        "code": "1234",
        "name": "송창훈",
        "ID": "sch990428",
        "PW": "12345",
        "spec": "명지대학교 컴퓨터공학과"
      },
  }),
  methods: {
    onEdit(){
      alert("수정이 완료되었습니다!");
    }
  },
};
</script>

<style scoped>
  .signupBtn {
    width: 48px;
    height: 32px;
    background-color: #e8a541;
    color: #ffffff;
    border: 3px;
    border-radius: 5px;
    font-size: 14px;
    text-align: center;
    cursor: pointer;
  }
  .text-info {
    color: #e84141;
    font-size: 12px;
    text-align: center;
  }
  .nav-menu {
    margin-left: 15px;
    text-decoration: none;
  }
</style>
