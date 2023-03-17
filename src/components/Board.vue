<script setup lang="ts">
import { ref } from 'vue';
let selected = ref('')
let history = ref<string[]>([]);
const rows = ['1', '2', '3', '4', '5', '6', '7', '8'].reverse();
const columns = ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H']
const getBoxColorClass = (i: number, k: number) => {
  if ((i + k) % 2 !== 0) {
    return 'white'
  } else {
    return 'black'
  }
}
const select = (boxName: string) => {
  console.log('Selecting', boxName)
  selected.value = boxName
  history.value.push(boxName)
}

const isSelected = (boxName: string) => {
  if (boxName === selected.value) {
    return 'selected'
  } else {
    return ''
  }
}
</script>

<template>
  <div class="board">
    <div class="grid">
      <template v-for="(row, rowIndex) in rows" :key="row">
        <template v-for="(column, columnIndex) in columns" :key="column">
          <div class="box" :id="column + row" :class="[getBoxColorClass(rowIndex, columnIndex), isSelected(column + row)]"
            @click="select(column + row)">
          </div>

        </template>
      </template>
    </div>
    <div class="history">
        {{ history.join(' > ') }}
    </div>
  </div>
</template>

<style scoped>
.board {
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
}
.grid {
  height: 100%;
  display: grid;
  grid-template-columns: auto auto auto auto auto auto auto auto;
}

.box.white {
  background-color: white;
}

.box.black {
  background-color: #efefef;
}

.box.selected {
  background-color: lightblue;
}

.box {
  border: 1px dotted black;
}
.history {
  padding: 10px;
  overflow: scroll;
  height: 50px;
}

.history::-webkit-scrollbar {
    display: none;
  }

@media screen and (max-width: 450px) {}
</style>
