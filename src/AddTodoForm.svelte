<script>
  export let addTodo;
  let todoText;
</script>

<div class="uk-width-1-2@m uk-card uk-card-default uk-padding">
  <fieldset class="uk-fieldset">
    <legend class="uk-legend">Enter todo item</legend>
    <div class="uk-margin">
      <input bind:value={todoText} class="uk-input" placeholder="Todo">
    </div>
  </fieldset>
  <button on:click={addTodo(todoText)} class="uk-button uk-button-default">Add Todo</button>
</div>
