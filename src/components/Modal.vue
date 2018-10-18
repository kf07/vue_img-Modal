<template lang="pug">
  transition(name="modal" apper)
    .modal.modal__overlay(@click.self="$emit('close')")
      button.closeBtn(@click="$emit('close')")
      .modal__window
        .modal__content
          slot
        .modal__footer
          .modal__btns
            vs-button.button(@click="$emit('prev')" vs-type="filled") 前
            vs-button.button(@click="$emit('next')" vs-type="filled") 次
            <!--button.button(@click="$emit('close')") 閉じる-->
</template>

<script>
  export default {
    name: "Modal"
  }
</script>

<style scoped lang="scss">
  .modal__overlay {
    display: flex;
    align-items: center;
    justify-content: center;
    position: fixed;
    z-index: 30;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
  }

  .modal__window {
    background: #fff;
    border-radius: 4px;
    overflow: hidden;
    position: relative;
  }

  .modal__content {
    padding: 10px 10px;
    width: 800px;
  }

  .modal__footer {
    background: #ccc;
    padding: 10px 10px;
    text-align: right;
  }

  .modal-enter-active, .modal-leave-active {
    transition: opacity 0.4s;
    .modal__window {
      transition: opacity 0.4s, transform 0.4s;
    }
  }

  .modal-leave-active {
    transition: opacity 0.6s ease 0.1s;
  }

  .modal-enter, .modal-leave-to {
    opacity: 0;

    .modal__window {
      opacity: 0;
      transform: translateY(-20px);
    }
  }
  .modal__btns {
    display: flex;
    justify-content: space-between;
  }

  .button {
    width: 80px;
  }

  .closeBtn {
    position: absolute;
    top: 0;
    right: 0;
    width: 30px;
    height: 30px;
    background-color: #fff;
    &::before {
      content: '';
      width: 30px;
      height: 2px;
      position: absolute;
      background-color: #fff;
      transform: rotate(45deg);
    }
  }

</style>
