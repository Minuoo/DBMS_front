<template>
    <nav>
        <router-link to="/project" class = "nav-menu">프로젝트</router-link>
        <router-link to="/employee" class = "nav-menu">직원</router-link>
        <router-link to="/devinfo" class = "nav-menu">경력관리</router-link>
        <router-link to="/mypage" class = "nav-menu">MY</router-link>
        <router-link to="/" class = "nav-menu">로그아웃</router-link>
    </nav>
    <h1 align = "center">{{$route.query.code}} 개발자 목록</h1>
    <table align = "center">
        <tr>
            <td>
                <select name = "">
                    <option value = "code">사번</option>
                    <option value = "code">직무</option>
                    <option value = "code">이름</option>
                </select>
            </td>
            <td><input type = "text" id = "id"></td>
            <td><input type = "button" class = "searchBtn" value = "검색"></td>
        </tr>
    </table>
    <table align = "center">
     <tr>
        <td><input type = "button" class = "btn" value = "추가"></td>
      <td><input type = "button" class = "btn" value = "제외" @click="delProj"></td>
    </tr>
</table>
    <table align = "center" border = "1">
        <tr>
            <td>선택</td>
            <td>사번</td>
            <td>직무</td>
            <td>이름</td>
        </tr>
        <tr v-for="(emp, i) in empTable" :key="i">
            <td><input type="checkbox" v-model= "empSelect[i]"></td>
            <td>{{ emp.ecode }}</td>
            <td>{{ emp.eGrp }}</td>
            <td @click="showDev(emp.ecode)">{{ emp.ename }}</td>
        </tr>
    </table>
    </template>
    
    <script>
    export default {
      data: () => ({
        tName: "김병대",
        empTable: [{ecode: "001", eGrp: "RD", ename: "김병대"}, 
        {ecode: "006", eGrp: "마케팅", ename: "정윤상"}, {ecode: "008", eGrp: "경영", ename: "위진영"}, 
        {ecode: "025", eGrp: "개발", ename: "문민우"}, {ecode: "051", eGrp: "개발", ename: "송창훈"}, ],
        empSelect: [false, false, false, false, false]
      }),
      methods: {
        showDev(c) {
            this.$router.push({
            name: "targetdevinfo",
            query: { code: c },
      });
        },
        delEmp() {
          for (let k = 0; k < this.empSelect.length; k++){
            if (this.empSelect[k]){
              this.empSelect.splice(k, 1);
              this.empTable.splice(k, 1);
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
    