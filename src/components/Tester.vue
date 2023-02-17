<template>
  <div id="test-container">
    <div id="button-container">
      <button 
      id="test-button-run" 
      class="test-button"
      @click="testOne">
      Run Test
    </button>
     <button 
      id="test-button-clear" 
      class="test-button clear-button"
      @click="clearData">
      Clear
    </button>
    </div>
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
      },
      {
        deviceId: 6,
        temperatureMeasureCode: "C",
        temperatureNumber: -21,
        runningState: 0
      },
      {
        deviceId: 7,
        temperatureMeasureCode: "C",
        temperatureNumber: -120,
        runningState: 1
      },
      {
        deviceId: 8,
        temperatureMeasureCode: "C",
        temperatureNumber: -120,
        runningState: null
      },
      {
        deviceId: 9,
        temperatureMeasureCode: "C",
        temperatureNumber: null,
        runningState: null
      },
      {
        deviceId: 10,
        temperatureMeasureCode: "C",
        temperatureNumber: null,
        runningState: 1
      }
      ],
      fatherDiv: null,
      deviceId: null,
      name: "Tester",
    };
  },
  components: {
  },
  computed: {
  }, 
  mounted() {
    this.fatherDiv = document.getElementById("button-container");
  },
  methods: {
    testOne() {
      this.deviceId = this.getrandomNumber();
      this.clearData();
      const updatedEl = this.createInfoElements();

      this.fatherDiv.appendChild(updatedEl);
    },
    clearData () {
      if (this.fatherDiv) {
        this.clearElementChildren(this.fatherDiv);
      };
    },
    createInfoElements() {
      const infoDiv = document.createElement('div');
      infoDiv.id = "info-div";
      infoDiv.innerText = `Test Sample for ${this.sampleData[this.deviceId].deviceId}`;

      const innerinfoDiv = document.createElement('div');
      innerinfoDiv.id = "data-list-container";

      const ulOfData = document.createElement("ul");
      ulOfData.id = "data-list";

      const currentDataObj = this.sampleData[this.deviceId];
      for(const val in currentDataObj) {
        const liItem = document.createElement('li');
        liItem.innerHTML = `<b>${val}</b>: ${currentDataObj[val]}`;
        ulOfData.appendChild(liItem);
      };

      innerinfoDiv.appendChild(ulOfData);
      infoDiv.appendChild(innerinfoDiv);

      this.createSampleOutputs(innerinfoDiv);


      return infoDiv;
      
    },
    clearElementChildren(el) {
      while (el.lastChild) {
        if (el.lastChild.id == "test-button-run"
        || el.lastChild.id == "test-button-clear") {
          return;
        };
        el.lastChild.remove()
      }
    },
    createSampleOutputs(el) {
      const output = document.createElement('p');
      const filteredData = this.tempFilter();
      output.innerHTML = `<b>Output Z:</b> ${filteredData} <br>`;

      const stateData = this.stateFilter();
      output.innerHTML += `<b>Output Y:</b> ${stateData}`;

      el.appendChild(output);
    },
    stateFilter () {
      const currentDataObj = this.sampleData[this.deviceId];
      if (currentDataObj.runningState === 1 &&
        currentDataObj.temperatureNumber != null &&
        currentDataObj.temperatureNumber != undefined
      ) { 
        return `<span class="sensor-pass">${currentDataObj.temperatureNumber}${currentDataObj.temperatureMeasureCode}</span>`
      } else {
        return '<span class="sensor-error">Sensor Error</span>';
      }
    },
    tempFilter () {
      const currentDataObj = this.sampleData[this.deviceId];
      if (currentDataObj.temperatureMeasureCode.toUpperCase() !== 'C' ||
        currentDataObj.temperatureNumber == null ||
        currentDataObj.temperatureNumber == undefined ||
        currentDataObj.temperatureNumber > 120 ||
        currentDataObj.temperatureNumber < -20 ) { 
          return '<span class="sensor-error">Sensor Error</span>';
      } else {
        return `<span class="sensor-pass">${currentDataObj.temperatureNumber}${currentDataObj.temperatureMeasureCode}</span>`
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
  margin: 25px;
}

.sensor-error {
  color: red;
}
.sensor-pass {
  color: green;
}

#data-list-container {
  text-align: center;
}

#data-list {
  width: 35%;
  display: inline-block;
  list-style-type: none;
  text-align: left;
}
</style>
