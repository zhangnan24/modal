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
  left: 0;
  top: 0;
  z-index: 999;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.3);

  .center {
    width: 1036px;
    height: 818px;
    margin: 60px auto 0;

    .head {
      position: relative;
      height: 50px;
      background: #fb621e;
      font-size: 20px;
      color: #fff;
      text-align: center;
      line-height: 50px;

      button {
        position: absolute;
        right: 15px;
        top: 8px;
        display: block;
        width: 34px;
        height: 34px;
        background: url(../../../public/img/dialogBtn.png) no-repeat;
        border: 0;
        padding: 0;
        outline: none;
        cursor: pointer;
        transition: transform 0.2s;
      }

      button:hover {
        transform: rotateZ(180deg);
      }
    }

    .body {
      overflow: hidden;
      height: 748px;
      background: #fff;
    }
  }
}
</style>
