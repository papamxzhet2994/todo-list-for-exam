<script>
    export let addTask = () => {};
  
    let newTask = "";
  
    function handleSubmit() {
      addTask(newTask);
      newTask = "";
    }
  
    function handleClear() {
      newTask = "";
    }
  </script>
  
  <form on:submit|preventDefault={handleSubmit}>
    <input type="text" bind:value={newTask} />
    <button type="submit">Добавить задачу</button>
    {#if newTask}
      <button type="button" on:click={handleClear}>Очистить</button>
    {/if}
  </form>
  
<style>
form {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  margin: auto;
  margin-top: 20px;
  margin-bottom: 20px;
  padding: 20px;
  border: none;
  border-radius: 10px;
  width: 500px;
  box-sizing: border-box;
  background-color: #222;
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
}

input {
  flex: 10;
  padding: 12px 16px;
  border-radius: 10px;
  border: none;
  font-size: 16px;
  width: 100%;
  box-sizing: border-box;
  background-color: #333;
  color: #fff;
  outline: none;
}

input::placeholder {
  color: #aaa;
}

button {
  padding: 10px 16px;
  border-radius: 10px;
  background-color: #ff3e00;
  color: #fff;
  border: none;
  cursor: pointer;
  width: 200px;
  font-size: 16px;
  margin-top: 20px;
  transition: all 0.2s ease-in-out;
}

button:hover {
  background-color: #ff5722;
}

button:active {
  transform: scale(0.98);
}

  </style>