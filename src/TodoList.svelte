<script>
  export let items;
</script>

<table class="uk-table uk-table-divider" id="done-table">
  <caption> Items Todo :</caption>
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
      </tr>
    {/each}
  </tbody>
</table>
