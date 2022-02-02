<script>
    import { createEventDispatcher } from "svelte"

    const dispatch = new createEventDispatcher()
    let todo = ''

    const clickHandle = () => {
        if (todo.length > 5) {
            dispatch('insert', {
                text: todo
            })
            todo = ''
        }
    }

</script>

<div class="add-todo">
    <input type="text" placeholder="Add your new todo" bind:value={todo}>
    <button type="button" on:click={clickHandle}>
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="#fff" class="bi bi-plus-lg" viewBox="0 0 16 16">
            <path fill-rule="evenodd" d="M8 2a.5.5 0 0 1 .5.5v5h5a.5.5 0 0 1 0 1h-5v5a.5.5 0 0 1-1 0v-5h-5a.5.5 0 0 1 0-1h5v-5A.5.5 0 0 1 8 2Z"/>
        </svg>
    </button>
</div>

<style>
    .add-todo {
        margin: 15px 0;
        display: flex;
        align-items: center;
        justify-content: space-between;
        column-gap: 5px;
    }
    .add-todo input {
        width: 100%;
        border: 1px solid #eee;
        border-radius: 4px;
        font-size: 14px;
        padding: 0 10px;
        height: 35px;
    }
    .add-todo button {
        background: #4b3eff;
        height: 35px;
        width: 50px;
        border-radius: 4px;
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;
    }
</style>