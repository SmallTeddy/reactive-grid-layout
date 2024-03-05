<template>
  <div class="main flex-col">
    <div class="icon flex-c">
      <img v-for="item in svgItems" :src="`./layout/${item}.svg`" :alt="item" @click="handleChangeLayout(item)">
    </div>
    <div class="layout">
      <div class="parent">
        <div v-if="svgItem.includes(1)" class="div1" :style="div1style"></div>
        <div v-if="svgItem.includes(1)" class="div2" :style="div2style"></div>
        <div v-if="svgItem.includes(2)" class="div3" :style="div3style"></div>
        <div v-if="svgItem.includes(3)" class="div4" :style="div4style"></div>
        <div v-if="svgItem.includes(4)" class="div5" :style="div5style"></div>
      </div>
    </div>
  </div>
</template>

<script lang='ts' setup>
import { ref, onMounted } from 'vue'

const resetSvgItems = () => ['layout01', 'layout02', 'layout03', 'split', 'layout04', 'layout05', 'layout06', 'split', 'layout07', 'layout08', 'layout09', 'layout10', 'split', 'layout11']
const svgItem = ref([1])
const svgItems = ref()
svgItems.value = resetSvgItems()

const div1style = ref({ gridArea: '' })
const div2style = ref({ gridArea: '' })
const div3style = ref({ gridArea: '' })
const div4style = ref({ gridArea: '' })
const div5style = ref({ gridArea: '' })


const handleChangeLayout = (item: string) => {
  if (item === 'split') return
  switch (item) {
    case 'layout01':
      div1style.value.gridArea = '1 / 1 / 7 / 3'
      div2style.value.gridArea = '1 / 3 / 7 / 7'
      svgItem.value = [1]
      break
    case 'layout02':
      div1style.value.gridArea = '1 / 1 / 7 / 5'
      div2style.value.gridArea = '1 / 5 / 7 / 7'
      svgItem.value = [1]
      break
    case 'layout03':
      div1style.value.gridArea = '1 / 1 / 3 / 7'
      div2style.value.gridArea = '3 / 1 / 7 / 7'
      svgItem.value = [1]
      break
    case 'layout04':
      div1style.value.gridArea = '1 / 1 / 7 / 3'
      div2style.value.gridArea = '1 / 3 / 4 / 7'
      div3style.value.gridArea = '4 / 3 / 7 / 7'
      svgItem.value = [1, 2]
      break
    case 'layout05':
      div1style.value.gridArea = '1 / 1 / 3 / 7'
      div2style.value.gridArea = '3 / 1 / 7 / 3'
      div3style.value.gridArea = '3 / 3 / 7 / 7'
      svgItem.value = [1, 2]
      break
    case 'layout06':
      div1style.value.gridArea = '1 / 1 / 3 / 7'
      div2style.value.gridArea = '3 / 1 / 7 / 5'
      div3style.value.gridArea = '3 / 5 / 7 / 7'
      svgItem.value = [1, 2]
      break
    case 'layout07':
      div1style.value.gridArea = '1 / 1 / 3 / 7'
      div2style.value.gridArea = '3 / 1 / 7 / 3'
      div3style.value.gridArea = '3 / 3 / 5 / 7'
      div4style.value.gridArea = '5 / 3 / 7 / 7'
      svgItem.value = [1, 2, 3]
      break
    case 'layout08':
      div1style.value.gridArea = '1 / 1 / 3 / 7'
      div2style.value.gridArea = '3 / 1 / 7 / 3'
      div3style.value.gridArea = '3 / 3 / 7 / 5'
      div4style.value.gridArea = '3 / 5 / 7 / 7'
      svgItem.value = [1, 2, 3]
      break
    case 'layout09':
      div1style.value.gridArea = '1 / 1 / 7 / 3'
      div2style.value.gridArea = '1 / 3 / 4 / 7'
      div3style.value.gridArea = '4 / 3 / 7 / 5'
      div4style.value.gridArea = '4 / 5 / 7 / 7'
      svgItem.value = [1, 2, 3]
      break
    case 'layout10':
      div1style.value.gridArea = '1 / 1 / 7 / 5'
      div2style.value.gridArea = '1 / 5 / 3 / 7'
      div3style.value.gridArea = '3 / 5 / 5 / 7'
      div4style.value.gridArea = '5 / 5 / 7 / 7'
      svgItem.value = [1, 2, 3]
      break
    case 'layout11':
      div1style.value.gridArea = '1 / 1 / 3 / 7'
      div2style.value.gridArea = '3 / 1 / 5 / 4'
      div3style.value.gridArea = '3 / 4 / 5 / 7'
      div4style.value.gridArea = '5 / 1 / 7 / 4'
      div5style.value.gridArea = '5 / 4 / 7 / 7'
      svgItem.value = [1, 2, 3, 4]
      break
  }
  svgItems.value = resetSvgItems()
  svgItems.value = svgItems.value.map(svg => svg.replace(item, `${item}-active`))
}

onMounted(() => {
  handleChangeLayout('layout01')
})
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
}

.flex {
  display: flex;
}

.flex-1 {
  flex: 1;
}

.flex-col {
  display: flex;
  flex-direction: column;
}

.flex-c {
  display: flex;
  justify-content: center;
  align-items: center;
}

.icon,
.icon img {
  cursor: pointer;
  height: 40px;
}

.layout {
  width: 100%;
  height: 800px;
}

.parent {
  width: 100%;
  height: 100%;
  display: grid;
  grid-template-columns: repeat(6, 1fr);
  grid-template-rows: repeat(6, 1fr);
  grid-column-gap: 0px;
  grid-row-gap: 0px;
}

.div1,
.div2,
.div3,
.div4,
.div5 {
  width: 100%;
  height: 100%;
}

.div1 {
  background: #74b9ff;
}

.div2 {
  background: #fab1a0;
}

.div3 {
  background: #ffeaa7;
}

.div4 {
  background: #55efc4;
}

.div5 {
  background: #e17055;
}
</style>
