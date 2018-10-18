<template lang="pug">
  div
    button(@click="index++") ボタン
    ul.imageList
      li.images(@click="openModal")
        img(src="../assets/modal_thumb01.jpg")
      li.images(@click="openModal")
        img(src="../assets/modal_thumb02.jpg")
      li.images(@click="openModal")
        img(src="../assets/modal_thumb03.jpg")
      li.images(@click="openModal")
        img(src="../assets/modal_thumb04.jpg")
      li.images(@click="openModal")
        img(src="../assets/modal_thumb05.jpg")
      li.images(@click="openModal")
        img(src="../assets/modal_thumb06.jpg")
      li.images(@click="openModal")
        img(src="../assets/modal_thumb07.jpg")
      li.images(@click="openModal")
        img(src="../assets/modal_thumb08.jpg")
      li.images(@click="openModal")
        img(src="../assets/modal_thumb09.jpg")
      li.images(@click="openModal")
        img(src="../assets/modal_thumb10.jpg")
    Modal(@close="closeModal" v-if="modal")
      img.modal__image(v-bind:src="require(`../assets/modal_img${index}.jpg`)")
</template>

<script>
  import Modal from "./Modal";

  export default {
    name: "index",
    components: {Modal},
    data() {
      return {
        modal: false,
        index: 1,
        imgPath: '',
      }
    },
    watch: {
      index: {
        handler: function(){
          const index = ('00' + this.index).slice(-2);
          this.index = index;
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
    width: 19.5%;
    cursor: pointer;
    margin: 0 0 8px;
    img {
      width: 100%;
      vertical-align: bottom;
    }
  }
  .modal__image {
    width: 100%;
  }

  .imageList {
    justify-content: space-between;
    margin: auto;
    width: 1400px;
    display: flex;
    flex-wrap: wrap;
    list-style: none;
  }
</style>
