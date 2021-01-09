.<template>
  <h2>Hi this is a To Do APP </h2>
  <label for="">Enter Your Title:</label><br>
  <input  @keyup.enter="addTodo" v-model="newTodo" type="text" class="todo-input" ><br>
  
  
    <table border="1">
     <tr>
          <td>ID</td>
          <td>Title</td>
          <td>Compelete</td>
          <td>Action</td>
       </tr>      
        <tr v-for="todo in todos"  :key="todo.id">
               <td>{{ todo.id }}</td>
               <td>{{ todo.title }}</td>
               <td  >Completed</td>
               <td class="remove" style="text-align:center"  >&times;</td>
         </tr>       
   </table>
     


  
</template>

<script>
export default {
   data() {
      return {
         newTodo: '',
         idForTodo: 4,
         todos:[
         {'id':1, 'title': 'Finish Vue ScreanCast', 'completed': false},
         
         {'id':2, 'title': 'Take Over Wold', 'completed': false},
         
         {'id':3, 'title': 'Failer Is better to success', 'completed': false}, 
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
            });
            this.newTodo = '';
            this.idForTodo++;
         }
         
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
</style>