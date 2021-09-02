<template>
  <div> 
    <TagInput v-model="tags" />
    <ul>
      <li v-for="tag in tags" :key="tag">{{ tag }}</li>
    </ul>
  </div>
</template>

<script>
import TagInput from "./components/TagInput.vue";

export default {
  name: 'App',
  components: {
    TagInput: TagInput,
  },
  data(){
    return {
      tags: ["hello", "app"],
    };
  },
};
</script>

<style lang="scss">
@import "~@/assets/scss/vendors/bootstrap-vue/index";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
