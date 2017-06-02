<template id="addTodo">
  <div class="addTodo form-group">
    <div class="col-sm-4 col-sm-offset-4">
      <input class="form-control input-sm" v-model="newtodo.title" type="text" name="" value="" placeholder="待办事项">
    </div>
    <input class="col-sm-1 btn btn-success btn-sm pull-left" @click="AddSth(newtodo)" type="button" name="" value="提交">
    <span class="col-sm-9" v-show="textFlagNull" style="color:red">*请填写内容</span>
  </div>
</template>

<style media="screen">
  .addTodo{
    margin-top: 20px;
  }
</style>

<script>
export default {
  name: 'addTodo',
  props: ['todos'],
  data () {
    return {
      newtodo: {title: null, flag: false, time: null},
      textFlagNull: false
    }
  },
  methods: {
    AddSth: function(newtodo){
      if(newtodo.title == null){
        this.textFlagNull = true;
      }else{
        this.textFlagNull = false;
        this.todos.push(newtodo);
        this.newtodo = {title: null, flag: false, time: null}
        }
    }
  }
}
</script>
