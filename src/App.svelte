<script>
  import TodoList from "./lib/TodoList.svelte";
  import AddTodo from "./lib/AddTodo.svelte";
  import { onMount } from "svelte";
  

  let tasks = [];
  let showDescription = true;

  function addTask(newTask) {
    tasks = [...tasks, { text: newTask, completed: false }];
    showDescription = false;
    saveTasks();
  }

  function removeTask(taskToRemove) {
    tasks = tasks.filter((task) => task !== taskToRemove);
    if (tasks.length === 0) {
      showDescription = true;
    }
    saveTasks();
  }

  const localStorageKey = "todoList";

  function saveTasks() {
    localStorage.setItem(localStorageKey, JSON.stringify(tasks));
  }

  function loadTasks() {
    const storedTasks = localStorage.getItem(localStorageKey);
    if (storedTasks) {
      tasks = JSON.parse(storedTasks);
      showDescription = false;
    }
    if (tasks.length === 0) {
      showDescription = true;
    }
  }

  onMount(() => {
    loadTasks();
  });
</script>


<a href="https://svelte.dev"><h1>Todo List</h1></a>
{#if showDescription}
    <p>Это список задач, который поможет вам организовать свои дела и не забыть о важных задачах. Начните добавлять новые задачи, используя форму ниже:</p>
{/if}
    <TodoList tasks={tasks} removeTask={removeTask} />
    <AddTodo addTask={addTask} />

<style>
h1 {
    text-transform: uppercase;
    font-family: "Roboto", sans-serif;
    color: #ff3e00;
    font-weight: 900;
    font-size: 40px;
    margin-bottom: 20px;
    background-color: black;
    justify-content: center;
    align-items: center;
    display: flex;
    max-width: 500px;
    margin: auto;
    border: 2px;
    border-radius: 30px;
    margin-bottom: 100px;
  }

  h1:hover {
    background-color: #ff3e00;
    box-shadow: 0px 5px 15px rgba(0, 0, 0, 0.3);
    color: black;
  }

a {
  text-decoration: none;
}

  p {
    font-family: "Roboto", sans-serif;
    font-size: 20px;
    margin-bottom: 50px;
    margin-top: 50px;
    text-align: center;
    max-width: 500px;
    margin: auto;
    color: #888;
  }

  @media (max-width: 768px) {
    h1 {
      font-size: 30px;
      margin-bottom: 10px;
      margin-top: 30px;
      max-width: 90%;
      border-radius: 20px;
      box-shadow: 0px 5px 15px rgba(0, 0, 0, 0.3);
    }

    p {
      font-size: 16px;
      margin-bottom: 30px;
      margin-top: 30px;
      max-width: 90%;
    }
  }
</style>
