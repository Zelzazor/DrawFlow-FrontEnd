<template>
  <div class="card-devices" >
     <div class="header">
        <h1>Number</h1>
     </div>
    <div class="body" >
       <span @click="Clicked"> Number:</span><input type="text" name="name" id="name">
     </div>
  </div>
</template>

<script>
export default {
  methods: {
    Clicked() {
      alert("hello-drawflow");
    }
  }
}
</script>

<style>
    input {
        width: 90%;
    }
    h1 {
      font-size: 22px;
    }
</style>

