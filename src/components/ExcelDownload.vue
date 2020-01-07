<template>
  <div>
    <div class="excel-btn-wrapper">
      <button class="excel-btn">엑셀 다운</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ExcelDownload"
};
</script>

<style lang="scss" scoped>
.excel-btn-wrapper {
  display: flex;
  justify-content: flex-end;
}

.excel-btn {
  width: 120px;
  margin-left: 5px;
  padding: 5px 8px;
  border: 2px solid black;
  border-radius: 5px;
  background-color: #555555;
  color: white;
  font-weight: bold;
}

.excel-btn:hover {
  background-color: black;
}
</style>
