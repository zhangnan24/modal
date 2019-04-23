<template>
  <section class="modal" v-show="visible" @click.stop="hideSelf">
    <div class="center" @click.stop>
      <div class="head">
        {{ title ? title : ''}}
        <button @click="hideSelf"></button>
      </div>
      <div class="body">
        <slot></slot>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    visible: {
      type: Boolean,
      required: true,
    },
    title: String,
  },
  methods: {
    hideSelf() {
      this.$emit('hide', false);
    },
  },
};
</script>

<style lang="less" scoped>
.modal {
  position: fixed;
  z-index: 999;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.3);
  display: flex;
  justify-content: center;
  align-items: center;

  .center {
    width: 1036px;
    height: 818px;

    .head {
      height: 50px;
      background: #fb621e;
      color:#fff;
      font-size: 20px;
      text-align: center;
      line-height:50px;
      position: relative;

      button {
        position: absolute;
        right: 15px;
        top: 8px;
        display: block;
        width: 34px;
        height: 34px;
        border: 0;
        padding: 0;
        outline: none;
        cursor: pointer;
        background: url(../../../public/img/dialogBtn.png) no-repeat;
        transition: transform .2s;
      }

      button:hover{
        transform: rotateZ(180deg);
      }
    }

    .body {
      height: 748px;
      background: #fff;
      overflow: hidden;
    }
  }
}
</style>
