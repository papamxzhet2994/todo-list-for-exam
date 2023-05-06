<script>
    export let tasks = [];
    export let removeTask = () => {};
  
    function toggleCompleted(task) {
      task.completed = !task.completed;
    }
  
    function handleRemove(task) {
      removeTask(task);
    }
  </script>
<ul>
    {#each tasks as task}
    <li class:completed={task.completed}>
        <label>
            <input type="checkbox" on:change={() => toggleCompleted(task)} />
            {task.text.replace(/\n/g, '<br/>')}
        </label>
        <button type="button" on:click={() => handleRemove(task)}>Удалить</button>
      </li>
      
    {/each}
  </ul>
  
  
<style>

ul {
  padding: 0;
}


li {
  cursor: pointer;
  list-style: none;
  padding: 20px;
  border: 2px solid #ccc;
  border-radius: 10px;
  margin-bottom: 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  box-sizing: border-box;
  background-color: #fff;
  font-size: 20px;
  font-weight: 400;
  font-family: 'Roboto', sans-serif;
  transition: all 0.2s ease-in-out;
  white-space: pre-wrap;
}

li:hover {
  box-shadow: 0px 5px 15px rgba(0, 0, 0, 0.1);
}

li.completed {
  background-color: rgba(255, 255, 255, 0.6);
  color: #888;
  box-shadow: none;
}

li.completed:hover {
  box-shadow: none;
}

li:last-of-type {
  margin-bottom: 0;
}

button {
  cursor: pointer;
  border: none;
  background-color: #ff3e00;
  color: white;
  border-radius: 10px;
  padding: 10px 20px;
  font-size: 16px;
  font-weight: 500;
  font-family: 'Roboto', sans-serif;
  transition: all 0.2s ease-in-out;
}

button:hover {
  background-color: #f33b00;
  box-shadow: 0px 5px 15px rgba(0, 0, 0, 0.1);
  transform: translateY(-2px);
}

button:active {
  transform: scale(0.98);
}   

input[type="checkbox"] {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  width: 20px;
  height: 20px;
  border: 2px solid #ccc;
  border-radius: 5px;
  position: relative;
  margin-right: 10px;
  cursor: pointer;
}

input[type="checkbox"]:before {
  content: "";
  display: block;
  width: 16px;
  height: 16px;
  position: absolute;
  top: 1px;
  left: 1px;
  border-radius: 3px;
  background-color: #fff;
  border: 2px solid #ccc;
  transition: all 0.2s ease-in-out;
}

input[type="checkbox"]:checked:before {
  content: "✓";
  display: flex;
  justify-content: center;
  align-items: center;
  color: #fff;
  font-size: 14px;
  font-weight: bold;
  background-color: #ff3e00;
  border-color: #ff3e00;
}




</style>