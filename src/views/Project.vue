<template>
<nav>
    <router-link to="/project" class = "nav-menu">프로젝트</router-link>
    <router-link to="/employee" class = "nav-menu">직원</router-link>
    <router-link to="/devinfo" class = "nav-menu">경력관리</router-link>
    <router-link to="/mypage" class = "nav-menu">MY</router-link>
    <router-link to="/" class = "nav-menu">로그아웃</router-link>
</nav>
<h1 align = "center">프로젝트 목록</h1>
<h3 align = "center">총 {{projTable.length}}개의 프로젝트가 진행 중입니다</h3>
<table align = "center">
  <tr>
    <td>
        <select name = "">
            <option value = "code">번호</option>
            <option value = "code">이름</option>
            <option value = "code">상태</option>
        </select>
    </td>
    <td><input type = "text" id = "id"></td>
    <td><input type = "button" class = "searchBtn" value = "검색"></td>
  </tr>
</table>
<table align = "center">
  <tr>
      <td><input type = "button" class = "btn" value = "추가"></td>
      <td><input type = "button" class = "btn" value = "삭제" @click="delProj"></td>
  </tr>
</table>
<table align = "center" border = "1">
  <tr class = "thead">
      <td>선택</td>
      <td>프로젝트번호</td>
      <td>프로젝트명</td>
      <td>착수일자</td>
      <td>종료일자</td>
      <td>발주처</td>
      <td>진행상태</td>
  </tr>
  <tr v-for="(project, i) in projTable" :key="i">
      <td><input v-model= "projSelect[i]" type="checkbox"></td>
      <td>{{ project.pcode }}</td>
      <td @click="showDev(project.pcode)">{{ project.pname }}</td>
      <td>{{ project.sdate }}</td>
      <td>{{ project.edate }}</td>
      <td>{{ project.cli }}</td>
      <td>{{ project.status }}</td>
  </tr>
</table>
</template>

<script>
export default {
  data: () => ({
    projTable: [{pcode: "A100", pname: "쇼미더머니", sdate: "2022-11-16", edate: "2022-12-01", cli: "MNET", status: "진행"}, 
    {pcode: "A101", pname: "무한도전", sdate: "2015-12-14", edate: "2021-12-31", cli: "MBC", status: "종료"}, 
    {pcode: "A102", pname: "아아아아", sdate: "2022-10-14", edate: "2022-12-31", cli: "KBSC", status: "중단"}],
    projSelect: [false, false, false]
  }),
  methods: {
    showDev(c) {
      this.$router.push({
        name: "projdevinfo",
        query: { code: c },
      });
    },
    delProj() {
      for (let k = 0; k < this.projSelect.length; k++){
        if (this.projSelect[k]){
          this.projSelect.splice(k, 1);
          this.projTable.splice(k, 1);
          k = -1;
        }
      }
    }
  },
};
</script>

<style scoped>
  .searchBtn {
    width: 48px;
    height: 24px;
    background-color: #e8a541;
    color: #ffffff;
    border: 3px;
    border-radius: 5px;
    font-size: 12px;
    text-align: center;
    cursor: pointer;
  }
  .btn {
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
  .nav-menu {
    margin-left: 15px;
    text-decoration: none;
  }
  
</style>
