<script>
    import Input from "./components/Input.svelte";
    import TodoList from "./components/TodoList.svelte"

    $: totalTodo = todos.filter(e => !e.completed).length

    let todos = [
        {
            id: 1,
            text: 'Buy a new gaming laptop',
            completed: false
        },
        {
            id: 2,
            text: 'Complete a previous task',
            completed: false
        },
        {
            id: 3,
            text: 'Create video for Youtube',
            completed: false
        },
        {
            id: 4,
            text: 'Create a new portfolio site',
            completed: false
        },
    ]

    const addTodo = (e) => {
        let lastId = todos[todos.length - 1]?.id ?? 1
        let newId = lastId += 1
        todos.push({
            id: newId,
            text: e.detail.text,
            completed: false
        })

        todos = todos
    }

    const clearAll = () => {
        todos = []
    }

    const removeTodo = (e) => {
        let todoId = e.detail.id -= 1

        todos.splice(todoId, 1)

        todos = todos
    }

    console.log(totalTodo)
</script>

<div class="todo-app">
    <div class="app-title">
        <h1>Todo App</h1>
    </div>
    <Input on:insert={addTodo} />
    <div class="todos">
        {#each todos as todo (todo.id)}
            {#if !todo.completed}
                <TodoList {todo} on:remove={removeTodo} />
            {/if}
        {/each}
    </div>
    {#if totalTodo > 0}
        <div class="footer">
            <div class="total">
                <span>You have {totalTodo} pending tasks</span>
            </div>
            <div class="clear-all">
                <button type="button" on:click={clearAll}>Clear All</button>
            </div>
        </div>
    {/if}
</div>


<style>
    .todo-app {
        box-shadow: rgba(50, 50, 93, 0.25) 0px 50px 100px -20px, rgba(0, 0, 0, 0.3) 0px 30px 60px -30px;
        background: #fff;
        border-radius: 6px;
        width: 100%;
        max-width: 400px;
        padding: 20px 10px;
    }
    .todo-app .app-title h1 {
        font-size: 20px;
        font-weight: 700;
    }
    .todos {
        display: flex;
        flex-direction: column-reverse;
        row-gap: 10px;
    }
    .footer {
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin-top: 15px;
    }
    .footer .total span {
        font-size: 12px;
        font-weight: 500;
    }
    .footer .clear-all button {
        background: #4b3eff;
        border-radius: 4px;
        color: #fff;
        font-weight: 500;
        font-size: 13px;
        cursor: pointer;
        padding: 4px 10px;
    }
</style>