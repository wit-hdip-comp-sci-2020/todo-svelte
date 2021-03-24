<script>
  import {v4 as uuidv4} from 'uuid';
  import Title from "./Title.svelte"
  import TodoList from "./TodoList.svelte";

  let todoText = "";
  let todoItems = [];
  let doneItems = [];

  function addTodo() {
    const todo = {
      text: todoText,
      date: new Date().toLocaleString("en-IE"),
      id: uuidv4()
    };
    todoItems.push(todo);
    todoItems = [...todoItems];
    todoText = "";
  }

  function deleteTodo(id) {
    const found = todoItems.findIndex((todo) => todo.id == id);
    const done = todoItems[found];
    todoItems.splice(found, 1);
    todoItems = [...todoItems];
    doneItems.push(done);
    doneItems = [...doneItems];
  }
</script>

<div class="uk-container">
  <Title title="Simple Todo List" subTitle="Fun Things to do"/>
  <div class="uk-width-1-2@m uk-card uk-card-default uk-padding">
    <fieldset class="uk-fieldset">
      <legend class="uk-legend">Enter todo item</legend>
      <div class="uk-margin">
        <input bind:value={todoText} class="uk-input" placeholder="Todo">
      </div>
    </fieldset>
    <button on:click={addTodo} class="uk-button uk-button-default">Add Todo</button>
  </div>
  <TodoList caption="Items Todo" items="{todoItems}" deleteSupport="true"/>
  <TodoList caption="Items Done" items="{doneItems}"/>
</div>
