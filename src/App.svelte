<script>
  let items = [{name: 'Manzanas', completed: false}, {name: 'Bananas', completed: false}, {name: 'Naranjas', completed: false}];
  let newItem = '';

  function addItem() {
    if (newItem.trim() !== '') {
      items = [...items, {name: newItem, completed: false}];
      newItem = '';
    }
  }

  function removeItem(index) {
    items = items.filter((_, i) => i !== index);
  }

  function toggleItem(index) {
    items[index].completed = !items[index].completed;
  }
</script>

<h1>Shopping List</h1>

<div class="input-group">
  <input type="text" bind:value={newItem} placeholder="Add item" class="input-item">
  <button on:click={addItem} class="btn-add">Add</button>
</div>

<ul class="list">
  {#each items as item, index}
    <li>
      {item.name} 
      <button on:click={() => toggleItem(index)} class:completed={item.completed}>{item.completed ? 'Desmarcar' : 'Marcar como completado'}</button>
      <button on:click={() => removeItem(index)} class="btn-remove">Remove</button>
    </li>
  {/each}
</ul>

<style>
  body {
    font-family: Arial, sans-serif;
    padding: 20px;
    background-color: #f5f5f5;
  }

  .input-group {
    margin-bottom: 20px;
  }

  .input-item {
    padding: 10px;
    width: 200px;
    border: 1px solid #ddd;
    border-radius: 4px;
  }

  .btn-add {
    padding: 10px 20px;
    margin-left: 10px;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }

  .btn-add:hover {
    background-color: #0056b3;
  }

  .list {
    list-style-type: none;
    padding: 0;
  }

  .list li {
    padding: 10px;
    margin-bottom: 10px;
    background-color: white;
    border: 1px solid #ddd;
    border-radius: 4px;
  }

  .completed {
    background-color: lightgreen;
    
  }

  .btn-toggle, .btn-remove {
    margin-left: 10px;
    padding: 5px 10px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }

  .btn-toggle {
    background-color: #ffc107;
    color: black;
  }

  .btn-remove {
    background-color: #dc3545;
    color: white;
  }

  .btn-toggle:hover {
    background-color: #e0a800;
  }

  .btn-remove:hover {
    background-color: #c82333;
  }
</style>







