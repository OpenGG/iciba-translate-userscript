<template>
  <div
    id="iciba-main"
    class="iciba-main"
    :style="internalStyle"
    v-show="visible">
    <div class="iciba-container">
      <div class="input-box">
        <input class="search-input" type="text" v-model="inputText">
        <div class="button-box">
          <div
            class="button"
            v-for="item in providers"
            :key="item.uniqName"
            :style="{ backgroundImage: `url('${item.icon}')` }">
          </div>
          <div class="button"></div>
        </div>
      </div>
      <div class="content-box">
        <p class="loading-tip" v-if="loading">
          加载中{{ loadingDots }}
        </p>
      </div>
    </div>
  </div>
</template>

<script lang="ts" src="./IcibaMain.ts"></script>
<style lang="less" scoped>
  @import '~assets/styles/variables.less';
  @import '~assets/styles/hardreset.less';

  .iciba-main {
    position: absolute;
    display: block;
    z-index: 9999;
    overflow: visible;
    border: none;
    box-shadow: none;
    box-sizing: border-box;
  }

  .iciba-container {
    position: absolute;
    top: 0;
    left: 0;
    width: auto;
    height: auto;
    max-width: 320px;
    border: none;
    background: @background-color;
    box-shadow: 0 0 8px 1px @box-shadow-color;
    letter-spacing: 0;
  }

  .input-box {
    @input-box-height: 28px;

    display: flex;
    flex-flow: row nowrap;
    border-bottom: 1px solid @light-border;
    height: @input-box-height + 1px;

    .search-input {
      flex: 1 1 auto;
      border: none;
      padding: 0 10px;
      line-height: @input-box-height;
      height: @input-box-height;
      z-index: 2;

      &:focus {
        outline: 2px solid @input-outline-color;
        outline-offset: -1px;
      }
    }

    .button-box {
      display: flex;
      flex-flow: row nowrap;
      flex: 1 1 auto;

      .button {
        width: @input-box-height + 1px;
        height: @input-box-height;
        border: none;
        border-left: 1px solid @light-border;
        background: none;
        z-index: 1;
        background-size: 16px;
        background-position: center;
        background-repeat: no-repeat;

        &:hover {
          background-color: @button-hover-color;
        }

        &:active {
          background-position: center calc(50% + 1px);
          background-color: @button-active-color;
          box-shadow: 0 0 5px #DDD inset;
        }
      }
    }
  }

  .content-box {
    padding: 10px;

    .loading-tip {
      margin: 0;
    }
  }
</style>
