<template>
  <div class="main">
    <b-list-group>
      <b-list-group-item v-for="produto in produtos" :key="produto.id">
        <div>
              <b-img class="my-image" :src="produto.image + `?r=${Math.random()}`"  alt="Circle image"></b-img>
              {{produto.name}} - {{produto.price}} 
        </div>  
      </b-list-group-item>
      
    </b-list-group>
  </div>
</template>

<script>
import Vue from "vue";
export default {
  name: "App",
  components: {},
  data() {
    return {
      produtos: []
    };
  },
  async mounted() {
    try {
      const { data } = await Vue.axios.get(
        "https://61fb022087801d0017a2c3c2.mockapi.io/api/v1/produtos"
      );

      this.produtos = [...data];
      // eslint-disable-next-line no-empty
    } catch (error) {}
  },
  methods: {
    
  },
};
</script>

<style>
.main {
  padding: 10px;
}
.my-image{

  max-width: 50px;
}
</style>
