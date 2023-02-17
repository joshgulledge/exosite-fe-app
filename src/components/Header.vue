<template>
  <img class="header" src="https://www.exosite.com/hubfs/Exosite_Logo_Color_RGB_White-cropped.svg" alt="Exosite_Logo_Color_RGB_White-cropped" @click=headerClick>
</template>

<script>

export default {
  data() {
    return {
      name: "Header",
    }
  },
  components: {
  },
  methods: {
    headerClick() {
      console.log("header clicked");
    }
  }
};
</script>

<style>
.header {
  background-color: black;
  width: 50%;
  padding: 10px;
  border-radius: 25px;
}
</style>
