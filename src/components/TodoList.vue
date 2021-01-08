.<template>
  <h2>Hi this is a To Do List APP </h2>
  <input v-model="newTodo" type="text" class="todo-input" ><button class="button"  type="submit">Add</button>
</template>

<script>
export default {

}
</script>

<style>
.todo-input{
   border-radius: 5px;
    border-color: #41b883;
    padding: 12px;
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
</style>