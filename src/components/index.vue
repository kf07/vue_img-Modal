<template lang="pug">
  div
    button(@click="index++") ボタン
    div.images(@click="openModal")
      img(src="../assets/modal_thumb01.jpg")
    Modal(@close="closeModal" v-if="modal")
      img.modal__image(v-bind:src='this.pathImg')
      p {{this.pathImg}}
</template>

<script>
  import Modal from "./Modal";

  export default {
    name: "index",
    components: {Modal},
    data() {
      return {
        modal: false,
        message: '',
        path : '../assets/modal_img',
        index: 1,
        imgPath: ''
      }
    },
    watch: {
      index: {
        handler: function(){
          const index = ('00' + this.index).slice(-2);
          // this.pathImg = `${this.path}${index}.jpg`;
          this.pathImg = require('../assets/modal_img01.jpg');
        },
        immediate: true
      }
    },
    methods: {
      openModal() {
        this.modal = true
      },
      closeModal() {
        this.modal = false
      }
    }
  }
</script>

<style scoped lang="scss">
  .images {
    width: 300px;
    cursor: pointer;
    img {
      width: 100%;
    }
  }
  .modal__image {
    width: 100%;
  }
</style>
