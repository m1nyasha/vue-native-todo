<template>
  <view>
    <view class="statusbar"></view>
    <text class="logo">
      Todo App
    </text>
    <Todos />
  </view>
</template>

<script>
  import Todos from './components/Todos'
  export default {
    components: {
      Todos
    }
  }
</script>

<style>
  .statusbar {
    background-color: #000;
    height: 20px;
  }
  .logo {
    font-size: 25px;
    text-align: center;
    margin-top: 10px;
  }
</style>
