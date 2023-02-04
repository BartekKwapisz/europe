<script> 
export default {
  data() {
    return {
      poland: {
        name: "Poland",
        flag:"/src/assets/Flag_of_Poland.svg"
      },
      germany: {
        name: "Germany",
        flag:"/src/assets/Flag_of_Germany.svg"
      },
      sliderValue: 3, 
      mapSrc: '/src/assets/map.svg'
    }
  },
  computed: { 
    selected_country() {
      return {
        name: this.poland.name,
        flag: this.poland.flag
      }
    },
    compared_country() {
      return {
        name: this.germany.name,
        flag: this.germany.flag
      }
    },
    relation(){ 
      let status = ["hostile","awful","bad","neutral","good","great","perfect"]
      return {
        status: status[this.sliderValue]
      }
    }
  },
  methods: {
    onClickHandler() {
      alert("hej")
    }
  },
  watch: {
     
  }
}
</script>

<template>
  <div class="grid-container"> 
    <div class="grid-item header"><img :src="mapSrc"/></div> 
    <div class="grid-item">{{selected_country.name}}</div>
    <div class="grid-item">relation</div>
    <div class="grid-item">{{compared_country.name}}</div> 
    <div class="grid-item"><img class="flag" v-bind:src="selected_country.flag"/></div>
    <div class="grid-item">
    <p>{{relation.status}}</p>
    </div>
     <div class="grid-item"><img class="flag" v-bind:src="compared_country.flag"/></div>
    <div class="grid-item">github</div>
    <div class="grid-item"><input type="range" v-model="sliderValue" min="0" max="6"/></div>
    <div class="grid-item"><button type="submit" @click="onClickHandler">submit</button></div>
  </div> 
</template>

<style scoped>

.flag{
  width: 100px;
}

.header {
  grid-row-start: 1;
  grid-row-end: 2;
  grid-column-start: 1;
  grid-column-end: 4;
  background-color: rgb(67, 155, 227);
}
</style>
