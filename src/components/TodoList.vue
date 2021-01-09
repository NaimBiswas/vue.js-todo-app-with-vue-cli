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
               
               
               <td   
                  @dblclick="editTodo(todo)"
                  v-if="!todo.edite"
                  >
                 
                     {{ todo.title }} 
                     <strong>
                        {{ todo.edite }}
                     </strong>  
                         
                   
                     
               </td>
                  <input v-else  type="text" v-model="todo.title">
               
               
               <td v-if="todos.completed = todos.completed" >
                  Complete <strong>{{ todos.completed }}</strong>
               </td>
               <td v-else>
                  Not Complete <strong>{{ todos.completed }}</strong>
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
               'completed': true,
               'edite': false,
               },
               
               {
                  'id':2, 
                  'title': 'Take Overg  Wold',
                  'completed': true,
                  'edite': false,
               },
              
         ],
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
     
            todo.edite = true;
            alert('this is working')
        
      },
      removeTodo(index){
         this.todos.splice(index, 1)
      }
      
   }

}
</script>

<style>
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
</style>