<template>
  <div>
    <div>
      <div class="input-wrapper name-input">
        <div class="input-title">유저 네임</div>
        <input type="text" v-model="userName" />
      </div>

      <div class="input-wrapper date-input">
        <div class="input-title">가입일</div>
        <input type="text" v-model="startDt" />
        <span class="tilde">~</span>
        <input type="text" v-model="endDt" />
        <span v-for="month in months" :key="month" class="month-wrapper">
          <div @click="monthSetting(month)" class="month-btn">{{ month }}M</div>
        </span>
      </div>
    </div>

    <div>
      <div class="input-wrapper id-input">
        <div class="input-title">유저 아이디</div>
        <input type="text" v-model="userId" />
      </div>

      <div class="input-wrapper id-input">
        <div class="input-title">유저 연락처</div>
        <input type="text" v-model="tel" />
      </div>

      <div class="input-wrapper id-input">
        <div class="input-title">유저 나이</div>
        <input type="text" v-model="age" />
      </div>

      <button @click="true" class="search-btn">검색</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "SearchForm",
  data() {
    return {
      userName: "",
      userId: "",
      age: "",
      tel: "",
      startDt: "",
      endDt: "",
      months: [1, 3, 6]
    };
  },
  methods: {
    formatDate(date) {
      var d = new Date(date),
        month = "" + (d.getMonth() + 1),
        day = "" + d.getDate(),
        year = d.getFullYear();

      if (month.length < 2) month = "0" + month;
      if (day.length < 2) day = "0" + day;

      return [year, month, day].join("-");
    },
    monthSetting(month) {
      var today = new Date();
      var monthLater = today.setMonth(today.getMonth() - month);

      this.endDt = this.formatDate(new Date());
      this.startDt = this.formatDate(monthLater);
    }
  }
};
</script>

<style lang="scss" scoped>
.input-wrapper {
  display: inline-flex;
  align-items: center;
  margin-bottom: 10px;
}

.input-title {
  font-weight: bold;
  font-size: 14px;
  width: 100px;
  display: inline-block;
  text-align: center;
}

.input-wrapper input {
  padding: 8px;
  border: 1px solid lightgray;
  border-radius: 5px;
  width: 150px;
}

.tilde {
  margin: 0 10px;
  font-weight: bold;
}

.month-wrapper {
  display: inline-flex;
}

.month-btn {
  display: flex;
  width: 30px;
  height: 30px;
  border: 2px solid darkgreen;
  border-radius: 5px;
  font-size: 14px;
  font-weight: bold;
  justify-content: center;
  align-items: center;
  margin-left: 10px;
}

.search-btn {
  width: 60px;
  margin-left: 5px;
  padding: 5px 8px;
  border: 2px solid black;
  border-radius: 5px;
  background-color: #555555;
  color: white;
  font-weight: bold;
}

.search-btn:hover {
  background-color: black;
}
</style>
