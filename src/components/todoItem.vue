<template id="todoItem">
  <div class="todoItem form-group row">
    <div class="btn mybtn col-sm-5 col-sm-offset-4">未完成<span class="caret pull-right"></span>
    </div>
    <div class="col-sm-5 col-sm-offset-4" style="padding-left: 0 !important;padding-right: 0 !important;">
      <ul>
        <li class="task" v-for="(todo, index) in todos" v-if="todo.title">
          <span class="" v-bind:class="[todo.flag ? 'liStyle' : '']">{{ todo.title }}
          <input class="btn btn-sm btn-success pull-right" @click="DeleteThis(todo,index)" type="button" name="" value="完成"></span>
        </li>
      </ul>
    </div>
    <div class="btn mybtn col-sm-5 col-sm-offset-4">已完成<span class="caret pull-right"></span>
    </div>
    <div class="col-sm-5 col-sm-offset-4" style="padding-left: 0 !important;padding-right: 0 !important;">
      <ul>
        <li class="task" v-for="finish in hasFinish">
          <p><b>任务详情：</b>{{ finish.title }}</p>
          <p>完成时间 {{ finish.time }} </p>
        </li>
      </ul>
    </div>
  </div>
</template>

<style media="screen">
  *{
    padding: 0;
    margin: 0;
  }
  ul > li{
    list-style: none;
  }
  .todoItem{
    margin-top: 60px;
  }
  .task{
    word-wrap: break-word;
    padding-left: 20px;
    padding-right: 20px;
    border: solid 1px #eee;
    border-top: transparent;
    line-height: 32px;
  }
  .liStyle{
    text-decoration: line-through;
  }
  .mybtn,
  .mybtn:hover{
    background-color: #26b6be !important;
    color: #fff !important;
  }
</style>

<script>
export default {
  name: 'todoItem',
  props: ['todos','hasFinish'],
  methods: {
    DeleteThis: function(todo,index){
      todo.flag = !todo.flag;
      this.todos.splice(index,1);

      //set time
      var timestamp = Date.parse(new Date());
      var date = new Date(timestamp);
      var M = (date.getMonth()+1 < 10 ? '0'+(date.getMonth()+1) : date.getMonth()+1) + '-';
      var D = date.getDate() + ' ';
      var h = date.getHours() + ':';
      var m = date.getMinutes() + ':';
      var s = date.getSeconds();
      var time_end = M + D + h + m + s;
      todo.time =time_end;
      this.hasFinish.push(todo);
    }
  },
  computed: {

  }
}

//
</script>
