<template>
  <div class="backdrop" @click.self="closeModal"><!-- .self -only click on self not childs -->
    <div class="modal" :class="{sale: theme === 'sale'}">
      <slot>
        <!-- we can pass here default content to be loaded if ther is no content in the parent template
          in this example h2 and text
        -->
      </slot>
      <div class="actions">
        <slot name="links"></slot>
      </div>
      <hr>
      <button @click="closeModal">CLOSE</button>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'ModalSlots',
    props:['theme'],
    methods: {
      closeModal () {
      this.$emit('closeModal')
      }
    }
  }
</script>

<style lang="scss" >
.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0,0,0,.5);
  width: 100%;
  height: 100%;
}
.modal {
  width: 900px;
  padding: 20px;
  margin: 100px auto;
  background: #fff;
  border-radius:10px;
  box-shadow: 0 0 10px rgba(0,0,0,.5);
  &.sale {
    background: crimson;
    color: #fff;
  }
  .actions {
    text-align: center;
    a {
      color:#fff;
      padding:5px 10px;
      border:1px solid #fff;
      margin:5px;
    }
  }
}

</style>