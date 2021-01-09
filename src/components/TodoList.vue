.<template>
  <h2>Hi this is a To Do APP </h2>
  <label for="">Enter Your Title:</label><br>
  <input  @keyup.enter="addTodo" v-model="newTodo" type="text" class="todo-input" ><br>
  
  
    <table border="1">
     <tr>
          <td>ID</td>
          <td>Title</td>
          <td>Compelete</td>
          <td>Delete</td>
       </tr>      
        <tr v-for="(todo, index) in todos"  :key="todo.id">
               <td>{{ todo.id }}</td>
               
               
               <td  class="title" 
                  @dblclick="editTodo(todo)"
                  v-if="!todo.edite"
                  >
                 
                     {{ todo.title }} 
                     <strong>
                        {{ todo.edite }}
                     </strong>  
                         
                   
                     
               </td>
                  <input
                  class="fff"
                   v-else  type="text" v-model="todo.title"
                  @blur="doneEdite(todo)"
                  @keyup.enter="doneEdite(todo)"
                  @keyup.esc="cancleEdite(todo)"
                  v-focus
                  >
               
               
               <td v-if="todo.completed" 
               class=""
               
               >
                 <button @click="cancleComplete(todo)">
                    Complete 
                  </button>
                  <strong>{{ todo.completed }}</strong>
               </td>
               
               <td v-else>
                 <button  @click="doneComplete(todo)"> Not Complete</button> <strong>{{ todo.completed }}</strong>
               </td>
               
               
               <td @click="removeTodo(index)" class="remove" style="text-align:center"  >&times;</td>
         </tr>       
   </table>
     


  
</template>

<script>
export default {
   data() {
      return {
         newTodo: '',
         idForTodo: 3,
         todos:[
               {
               'id':1,
               'title': 'Finish Vue ScreanCast', 
               'completed': false,
               'edite': false,
               },
               
               {
                  'id':2, 
                  'title': 'Take Overg  Wold',
                  'completed': false,
                  'edite': false,
               },
              
         ],
      }
      
   },
   directives:{
     focus:{
        inserted(el){
           el.focus()
        }
     } 
   },
   methods:{
      addTodo(){
         if(!this.newTodo == ''){
            this.todos.push({
               id: this.idForTodo,
               title: this.newTodo,
               completed: false,
               edite: true,
            });
            this.newTodo = '';
            this.idForTodo++;
         }
      },
      editTodo(todo){
         this.beforeEditCache = todo.title;
            todo.edite = true;
           
        
      },
      removeTodo(index){
         this.todos.splice(index, 1)
      },
      doneEdite(todo){
         if(todo.title.trim().length == 0){
            todo.title = this.beforeEditCache
         }
            todo.edite = false;
      },
      cancleEdite(todo){
         todo.title = this.beforeEditCache
         todo.edite = false;
      },
      doneComplete(todo){
         todo.completed = true;
      },
      cancleComplete(todo){
          todo.completed = false;
      }
      
   }

}
</script>

<style>
.title{
   width: 600px;
}
.fff{
   
    margin-top: 10px;
    padding: 2px;

}
.todo-input{
   border-radius: 5px;
    border-color: #41b883;
    padding: 10px;
    padding-left: 100px;
}
.button {
   
    text-align: cem;
    text-align: center;
    padding-right: 30px;
    padding: 11px;
    border-radius: 8px;
    background: #41b883;
    padding-right: 20px;
    padding-left: 20px;
    color: #fff;
    text-transform: uppercase;
    font-size: 14px;
    font-weight: 700;
}
.button:hover{
   cursor: pointer;
}
table{
   margin: 0 auto;
   margin-top: 50px;
   text-align: left;
}
.remove{
   cursor: pointer;
   color: red;
   font-size: 22px;
}
input{
   font-size: 18px;
}
td{
   padding: 9px;
   
}

</style>