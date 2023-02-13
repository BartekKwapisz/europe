<script> 
import SvgMap from '/src/assets/SvgMap.vue';
export default {
  components: { 
    SvgMap
  },
  data() {
    return {
      poland: {
        name: "Poland",
        flag: "/src/assets/Flag_of_Poland.svg"
      },
      germany: {
        name: "Germany",
        flag: "/src/assets/Flag_of_Germany.svg"
      },
      sliderValue: 3,
      mapSrc: '/src/assets/map2.svg',
      countries: ["Russia", "Kaliningrad", "Turkey", "Germany", "GreatBritain", "France", "Italy", "Spain", "Ukraine", "Poland", "Romania", "Netherlands", "Belgium", "CzechRepublic", "Greece", "Portugal", "Sweden", "Hungary", "Belarus", "Austria", "Switzerland", "Bulgaria", "Denmark", "Greenland", "Finland", "Slovakia", "Norway", "Ireland", "Croatia", "Georgia", "Cyprus", "Armenia", "Serbia", "Montenegro", "Kazakhstan", "Azerbaijan", "Moldova", "Bosnia", "Albania", "Lithuania", "FYROM", "Slovenia", "Latvia", "Estonia", "Luxembourg", "Malta", "Iceland", "Andorra", "Monaco", "Liechtenstein", "SanMarino"],
    }
  },
  methods: {
    //MAP:
    // from https://codepen.io/BartekKwapisz/pen/podPbWy
    // first assign on mouse over action to every country separetely
    // for(let i = 0; i <countries.length; i++) {
    //   document.getElementById(countries[i]).onmouseover = function () { color(countries[i]) };
    // }; -> use mounted or ref

    // then fire function that will change the name of the compared country on the right
    // function color(country){
    //   document.getElementById("subtitle").innerHTML = selectedCountry;
    // }

    // we also need to assign function that will change selected country on left click and another to lock compared country

    //FLAGS: just change flags when the name changes, this one is easy

    //FIREBASE: take data from firebase to color map each time country is selected and compared; update data every time user submits his assesment (take current score and number of votes, add the new vote to number of votes and new score and divide by number of votes -> then update database)
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
    let status = ["hostile", "awful", "bad", "neutral", "good", "great", "perfect"];
    let color = ["red", "orange", "Bisque", "#d8eafd", "DarkSeaGreen", "GreenYellow", "lime"]
    return {
      status: status[this.sliderValue],
      color: color[this.sliderValue]
    }
  }
},
methods: {
  onClickHandler() {
    alert("hej")
  }
},
created: {

},
watch: {

}
}
</script>

<template>
  <div class="grid-container">
    <div class="grid-item header">
      <SvgMap />  
    </div>
    <div class="grid-item">{{ selected_country.name }}</div>
    <div class="grid-item">relation:
      
    </div>
    <div class="grid-item">{{ compared_country.name }}</div>
    <div class="grid-item"><img class="flag" v-bind:src="selected_country.flag" /></div>
    <div class="grid-item" :style="{ backgroundColor: relation.color }">
      <p>{{ relation.status }}</p>
    </div>
    <div class="grid-item"><img class="flag" v-bind:src="compared_country.flag" /></div>
    <div class="grid-item"><a href="https://github.com/BartekKwapisz/europe" target="_blank">github</a></div>
    <div class="grid-item"><input type="range" v-model="sliderValue" min="0" max="6" /></div>
    <div class="grid-item"><button type="submit" @click="onClickHandler">submit</button></div>
  </div>
</template>

<style scoped>
.flag {
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
