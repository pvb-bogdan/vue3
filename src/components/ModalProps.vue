<template>
  <div class="backdrop" @click.self="closeModal"><!-- .self -only click on self not childs -->
    <div class="modal" :class="{sale: theme === 'sale'}">
      <h2>{{title}}</h2>
      <p>{{text}}</p>
      <hr>
      <button @click="closeModal">CLOSE</button>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Modal',
    props:['title', 'theme', 'text'],
    methods: {
      closeModal () {
      this.$emit('closeModal')
      }
    }
  }
</script>

<style lang="scss" scoped>
.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0,0,0,.5);
  width: 100%;
  height: 100%;
}
.modal {
  width: 400px;
  padding: 20px;
  margin: 100px auto;
  background: #fff;
  border-radius:10px;
  &.sale {
    background: crimson;
    color: #fff;
  }
}

</style>