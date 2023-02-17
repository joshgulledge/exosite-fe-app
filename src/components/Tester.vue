<template>
  <div id="test-container">
    <button 
      id="test-button-one" 
      class="test-button"
      @click="testOne">
      Hello Button
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      sampleData: [
        {
        deviceId: 1,
        temperatureMeasureCode: "C",
        temperatureNumber: 25,
        runningState: 1
      },
      {
        deviceId: 2,
        temperatureMeasureCode: "C",
        temperatureNumber: 125,
        runningState: 1
      },
      {
        deviceId: 3,
        temperatureMeasureCode: "C",
        temperatureNumber: 55,
        runningState: 0
      },
      {
        deviceId: 4,
        temperatureMeasureCode: "C",
        temperatureNumber: 99,
        runningState: 1
      },
      {
        deviceId: 5,
        temperatureMeasureCode: "C",
        temperatureNumber: 20,
        runningState: 1
      }
      ],
      name: "Tester",
    };
  },
  components: {
  },
  computed: {
  }, 
  mounted() {
  },
  methods: {
    testOne() {
      const fatherDiv = document.getElementById("test-container");      
      if (fatherDiv) {
        this.clearElementChildren(fatherDiv);
      };

      const infoDiv = document.createElement('div');
      infoDiv.id = "info-inner";
      const updatedEl = this.createInfoElements(infoDiv);
      fatherDiv.appendChild(updatedEl);
    },
    createInfoElements(el) {
      const rando = this.getrandomNumber();
      const infoPar = document.createElement('p');
      infoPar.innerText = `Test Sample for ${this.sampleData[rando].deviceId}`;
      el.appendChild(infoPar);
      return el;
      
    },
    clearElementChildren(el) {
      while (el.lastChild) {
        if (el.lastChild.id == "test-button-one") return;
        el.lastChild.remove()
      }
    },
    getrandomNumber() {
      return Math.floor(Math.random() * this.sampleData.length);
    }
  },
};
</script>

<style>
.test-button {
  width: 25%;
  min-height: 50px;
  background-color: black;
  color: white;
}
</style>
