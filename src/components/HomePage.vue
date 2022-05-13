<script setup>
import ButtonTitle from "./ButtonTitle.vue";
import Header from "./Header.vue";
import Content from "./Content.vue";
import List from "./List.vue";
</script>

<script>
export default {
  data() {
    return { //la posada per defecte és la d'episodis
      url: 'https://rickandmortyapi.com/api/episode',
    }
  },
  methods: { //Al mètode li passem una url i canvia el valor de la variable
    onClick(url) {
      this.url = url
    }
  },
  props: ['name']
}
</script>

<template>
  <Header> 
    <ButtonTitle name="Episodes" @click="onClick('https://rickandmortyapi.com/api/episode')" />
    <ButtonTitle name="Characters" @click="onClick('https://rickandmortyapi.com/api/character')" />
    <ButtonTitle name="Locations" @click="onClick('https://rickandmortyapi.com/api/location')" />
  </Header>

  <Content>
    <List :url="url" />
  </Content>
  <!-- <RickSection>
    <Rick :src="assets.rick" />
  </RickSection> -->
</template>
