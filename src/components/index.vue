<template lang="pug">
  div
    ul.imageList
      li.images(v-for="(item,index) in lists" v-bind:key="item.id" v-on:click="openModal(index)")
        img.modal__image(v-bind:src="require(`../assets/modal_thumb${item.img}.jpg`)")
    Modal(@close="closeModal" v-if="modal" @next="nextModal" @prev="prevModal")
      img.modal__image(v-bind:src="require(`../assets/modal_img${index2}.jpg`)")
</template>

<script>
  import Modal from "./Modal";

  export default {
    name: "index",
    components: {Modal},
    data() {
      return {
        modal: false,
        index: 1,　//表示する画像のindex
        imgPath: '',　
        lists: [
          {
            id:1,
            img: '01',
          },
          {
            id:2,
            img: '02',
          },
          {
            id:3,
            img: '03',
          },
          {
            id:4,
            img: '04',
          },
          {
            id:5,
            img: '05',
          },
          {
            id:6,
            img: '06',
          },{
            id:7,
            img: '07',
          },
          {
            id:8,
            img: '08',
          },
          {
            id:9,
            img: '09',
          },
          {
            id:10,
            img: '10',
          }
        ],
        index2 :0　//表示する画像のindexの0埋め
      }
    },
    watch: {
      index: {
        handler: function(){
          const index = ('00' + this.index).slice(-2);
          this.index2 = index;
        },
        immediate: true
      }
    },
    methods: {
      openModal(index) {
        this.index = index +1;
        this.modal = true;
      },
      closeModal() {
        this.modal = false
      },
      nextModal() {
        if (this.index < 10 ) {
          this.index += 1;
        } else {
          this.index = 1;
        }
      },
      prevModal() {
        if (this.index > 1 ) {
          this.index -= 1;
        }else {
          this.index = 10;
        }
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
    padding: 0;
  }
</style>
