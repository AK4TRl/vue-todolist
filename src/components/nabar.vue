<template id="nabar">
  <div class="nav nav-tabs nav-justified mynav">
    <h1>Task<span v-show="heading">({{heading}})</span></h1>
  </div>
</template>

<style>
  .mynav{
    background-color: #26b6be;
    color: #fff;
  }
</style>
<script>
import todoItem from './todoItem'
export default {
  name: 'nabar',
  props:['heading'],
  components: {
    todoItem
  }
}
</script>
