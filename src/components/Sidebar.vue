<script setup lang="ts">

</script>

<template>
  <div class="sidebar">
    <div v-for="n in 8" :key="n" class="sidebar-item">
      Sidebar item {{ n }}
    </div>
  </div>
</template>

<style scoped>
.sidebar {
  width: 100%;
  border-right: 1px dotted black;
  max-width: 300px;
  display: flex;
  flex-direction: column;
}

.sidebar-item {
  padding: 20px 20px;
  border-bottom: 1px dotted grey;
  display: block;
  cursor: pointer;
  font-size: 16px;
}


@media screen and (min-width: 450px) {
  .sidebar-item:hover {
    box-shadow: 1px 1px gray;
    font-size: 17px;
  }
}

@media screen and (max-width: 450px) {
  .sidebar {
    border-top: 1px dotted black;
    border-right: none;
    max-height: 300px;
    max-width: 100%;
    overflow: scroll;
  }

  .sidebar::-webkit-scrollbar {
    display: none;
  }
}
</style>
