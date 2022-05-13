<script>
export default {
  props: ['url'],
  data() {
    return {
      items: [],
      count: 0
    }
  },
  methods: {
    async fetchUrl(url) {
      try {
        const response = await fetch(url);
        const { results, info } = await response.json();

        this.items = results;
        this.count = info.count;
      } catch (error) {
        console.log(error)
      }
    }/*
    nextPage(){
      this.$router.push('15');
    }*/
  },
  async mounted() {
    await this.fetchUrl(this.url)
  },
  watch: {
    async url(newUrl) {
      await this.fetchUrl(newUrl)
    },
    count(newCount, oldCount) {
      console.log(`Proveta. S'ha actualitzat el valor de count. Ans era ${oldCount} i ara es ${newCount}`)
    }
  },
}
</script>

<template>
  <h2>Rick and Morty series has {{ count }} {{ url.replace("https://rickandmortyapi.com/api/", "") }}s</h2>
  <div class="characters">
    <ul class="list">
      <li class="list-item" v-for="item in items" :key="item.name">
        {{ item.name }}
      </li>
    </ul>
  </div>
</template>

<style scoped>
  h2 {
    color: rgb(255, 169, 169);
  }
  .characters{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }
  .list {
    max-width: 65%;
  }
</style>
