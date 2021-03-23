<script>
  let todoText = "";
  let todoItems = [];
  let doneItems = [];

  function uuidv4() {
    return "xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx".replace(/[xy]/g, function (c) {
      var r = Math.random() * 16 | 0, v = c == "x" ? r : (r & 0x3 | 0x8);
      return v.toString(16);
    });
  }

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
  <div class="uk-flex uk-flex-center uk-flex-middle uk-margin">
    <div class="uk-width-2-3@m uk-card uk-card-default uk-padding-small uk-text-center">
      <div class="title"> Simple Todo List</div>
      <div class="uk-text-muted uk-text-small">Fun things to do</div>
    </div>
  </div>
  <div class="uk-width-1-2@m uk-card uk-card-default uk-padding">
    <fieldset class="uk-fieldset">
      <legend class="uk-legend">Enter todo item</legend>
      <div class="uk-margin">
        <input bind:value={todoText} class="uk-input" placeholder="Todo">
      </div>
    </fieldset>
    <button on:click={addTodo} class="uk-button uk-button-default">Add Todo</button>
  </div>
  <table class="uk-table uk-table-divider">
    <caption> Items To Do :</caption>
    <thead>
      <tr>
        <th>Task</th>
        <th>Date</th>
      </tr>
    </thead>
    <tbody>
      {#each todoItems as todo}
        <tr>
          <td> {todo.text} </td>
          <td> {todo.date} </td>
          <button on:click={deleteTodo(todo.id)}  class="uk-button uk-button-default">Delete</button>
        </tr>
      {/each}
    </tbody>
  </table>
  <table class="uk-table uk-table-divider" id="done-table">
    <caption> Items Completed :</caption>
    <thead>
      <tr>
        <th>Task</th>
        <th>Date</th>
      </tr>
    </thead>
    <tbody>
      {#each doneItems as todo}
        <tr>
          <td> {todo.text} </td>
          <td> {todo.date}</td>
        </tr>
      {/each}
    </tbody>
  </table>
</div>
