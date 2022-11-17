<template>
<nav>
    <router-link to="/project" class = "nav-menu">프로젝트</router-link>
    <router-link to="/employee" class = "nav-menu">직원</router-link>
    <router-link to="/devinfo" class = "nav-menu">경력관리</router-link>
    <router-link to="/mypage" class = "nav-menu">MY</router-link>
    <router-link to="/" class = "nav-menu">로그아웃</router-link>
</nav>
  <h1 align = "center">개발자 경력관리</h1>
    <table align = "center">
        <tr>
            <td>
                <select name = "">
                    <option value = "code">사번</option>
                    <option value = "code">경력</option>
                    <option value = "code">개발자 등급</option>
                </select>
            </td>
            <td><input type = "text" id = "id"></td>
            <td><input type = "button" value = "검색"></td>
        </tr>
    </table>
    <table align = "center">
      <tr>
      <td><input type = "button" class = "btn" value = "저장" @click="save"></td>
    </tr>
    </table>
    <table align = "center" border = "1">
        <tr>
            <td>사번</td>
            <td>이름</td>
            <td>경력</td>
            <td>개발자 등급</td>
            <td>경험한 기술</td>
        </tr>
        <tr v-for="(dev, i) in devInfoTable" :key="i">
            <td>{{dev.ecode}}</td>
            <td>{{dev.dname}}</td>
            <td><textarea v-model="dev.career"></textarea></td>
            <td><select v-model="dev.grade" @change="change" >
              <option value = "수">수</option>
              <option value = "우">우</option>
              <option value = "미">미</option>
              <option value = "양">양</option>
              <option value = "가">가</option>
            </select></td>
            <td><textarea v-model="dev.skillset"></textarea></td>

        </tr>
    </table>
</template>

<script>
export default {
  data: () => ({
    devInfoTable: [{"ecode":"001", "dname":"송창훈", "career":"편의점 2년", "grade":"우", "skillset":"C, C++, C#, JAVA, JavaScript"}]
  }),
  methods: {
    save() {
      console.log(this.devInfoTable)
    }
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
  }
  .text-info {
    color: #e84141;
    font-size: 12px;
    text-align: center;
  }
  textarea{
    font-family: Avenir, Helvetica, Arial, sans-serif;
    font-size: 14px;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }
  .nav-menu {
    text-decoration: none;
    margin-left: 15px;
  }
  .nav-menu:active {
    color: #e8a541;
  }
</style>
