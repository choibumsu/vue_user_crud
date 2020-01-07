<template>
  <div>
    <page-title :title="title"></page-title>
    <search-form></search-form>
    <excel-download></excel-download>
    <user-table :userList="userList"></user-table>
  </div>
</template>

<script>
import axios from "axios";

import PageTitle from "@/components/PageTitle.vue";
import ExcelDownload from "@/components/ExcelDownload.vue";
import SearchForm from "@/components/SearchForm.vue";
import UserTable from "@/components/UserTable.vue";

export default {
  name: "userList",
  components: {
    PageTitle,
    ExcelDownload,
    SearchForm,
    UserTable
  },
  data() {
    return {
      title: "회원 리스트",
      userList: []
    };
  },
  created() {
    const userListAPI = axios.create({
      baseURL: window.baseUrl
    });

    var defaultCondition =
      "?age=&end_dt=&pageCon=10&pageNum=1&start_dt=&tel=&userSortDirection=ASC&userSortItem=user_seq&user_id=&user_name=&view_cnt=";
    userListAPI
      .get(`v1/chunjae/user/selectUser/` + defaultCondition)
      .then(response => {
        this.userList = response.data.data.rows;
        console.log(this.userList);
      })
      .catch(error => {
        console.log(error);
      });
  }
};
</script>

<style lang="scss" scoped></style>
