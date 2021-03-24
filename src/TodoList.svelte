<script>
  export let caption;
  export let items;
  export let deleteHandler = null;
</script>

<table class="uk-table uk-table-divider" id="done-table">
  <caption> {caption} :</caption>
  <thead>
    <tr>
      <th>Task</th>
      <th>Date</th>
    </tr>
  </thead>
  <tbody>
    {#each items as todo}
      <tr>
        <td> {todo.text} </td>
        <td> {todo.date}</td>
        {#if deleteHandler}
          <button on:click={deleteHandler(todo.id)} class="uk-button uk-button-default">Delete</button>
        {/if}
      </tr>
    {/each}
  </tbody>
</table>
