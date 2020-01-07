<template>
  <div>
    {{ userList }}
  </div>
</template>

<script>
export default {
  name: "UserTable",
  props: {
    userList: Array
  }
};
</script>

<style lang="scss" scoped></style>
