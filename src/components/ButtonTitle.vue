<script>
export default {
  props: ['name'], //li passem l'atribut nom
  data() {
    return {}
  }
}
</script>

<template>
  <button class="button-title">{{ name }}</button>
</template>

 <!--- Scoped pa que només s'apliquin els estils aneste component --> 
<style scoped> 
  .button-title {
    border-radius: 6px;
    padding: 16px 32px;
    cursor: pointer;
    font-size: 32px;
  }
  @keyframes changeColor {
  0% {
    color: aqua;
    border: 1px solid aqua;
  }
  50% {
    color: rgb(255, 169, 169);
    border: 1px solid rgb(255, 169, 169);
  }
  100% {
    color: #FF9225;
    border: 1px solid #FF9225;
  }
}
.button-title:hover {
  animation-name: changeColor;
  animation-iteration-count: infinite;
  animation-duration: 3s;
}
</style>
