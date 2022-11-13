<template>
  <div>
    <header class="d-flex py-4 "></header>
    <div class="verticalLine">
      <Nuxt />
    </div>
  </div>
</template>

<script>
export default {
  name: "default"
}
</script>

<style scoped>

.d-flex{
  border-bottom: 1px solid lightgrey;
  box-shadow: 0px 2px 20px rgba(0, 0, 0, 0.08);

}

.line{
  position: absolute;
  width: 8000px;
  height: 0px;
  margin-left: -266px;
  top: 60px;

  border: 1px solid #EBEDF5;
  transform: rotate(90deg);
}

.verticalLine {
  border-left: thin solid lightgrey;
  margin-left: 15%;
  padding-left: 4%;
}


</style>
