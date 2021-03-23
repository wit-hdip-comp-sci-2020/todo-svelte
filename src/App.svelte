<script>
  let todoText = "";
  let todoItems = [];

  function addTodo() {
    const todo = {
      text: todoText,
      date: new Date().toLocaleString("en-IE"),
    };
    todoItems.push(todo);
    todoItems = [...todoItems];
    todoText = "";
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
        </tr>
      {/each}
    </tbody>
  </table>
</div>
