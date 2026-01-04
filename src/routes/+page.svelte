<script lang="ts">
    let tasks = $state([
        { id: 1, text: 'Task 1', completed: false },
        { id: 2, text: 'Task 2', completed: false },
        { id: 3, text: 'Task 3', completed: false }
    ])

    const onClickDelete = (id: number) => {
        tasks = tasks.filter(task => task.id !== id);
    }

    let text = $state('');

    const onChangeText = (e: Event & { target: HTMLInputElement }) => {
    text = e.target.value;
}

    const onSubmit = (e: Event) => {
        tasks.push({ id: tasks.length + 1, text: text, completed: false });
        text = '';
    }
</script>

<h1>To Do List</h1>

<form>
    <input type="text" placeholder="Add a new task" bind:value={text}/>
    <button type="submit" onclick={onSubmit}>Add</button>s
</form>



{#each tasks as task}
    <li>{task.text} <button onclick={() => onClickDelete(task.id)}>Delete</button></li>
{/each}

<style>
    form {
        display: flex;
        gap: 10px;
    }

    input {
        width: 80%;
        padding: 10px;
        border: 1px solid #ccc;
        border-radius: 5px;
    }

    button {
        width: 20%;
        padding: 10px;
        border: 1px solid #ccc;
        border-radius: 5px;
        background-color: #007bff;
        color: white;
    }

    ul {
        list-style-type: none;
        padding: 0;
    }

    li {
        padding: 10px;
        border: 1px solid #ccc;
        border-radius: 5px;

        display: flex;
        justify-content: space-between;
        align-items: center;
    }
</style>