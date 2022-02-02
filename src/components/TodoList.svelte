<script>
    import { createEventDispatcher } from "svelte";

    const dispatch = new createEventDispatcher()
    export let todo

    const clickHandle = () => {
        dispatch('remove', todo)
    }
</script>

<div class="todo">
    <div class="text">
        {todo.text}
    </div>
    <div class="remove" on:click={clickHandle}>
        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="#fff" class="bi bi-trash3-fill" viewBox="0 0 16 16">
            <path fill-rule="evenodd" d="M6 1.5a.5.5 0 0 1 .5-.5h3a.5.5 0 0 1 .5.5v1H6v-1Zm5 0v1h3.5a.5.5 0 0 1 0 1h-.538l-.853 10.66A2 2 0 0 1 11.115 16h-6.23a2 2 0 0 1-1.994-1.84L2.038 3.5H1.5a.5.5 0 0 1 0-1H5v-1A1.5 1.5 0 0 1 6.5 0h3A1.5 1.5 0 0 1 11 1.5ZM4.5 5.029a.5.5 0 1 1 .998-.06l.5 8.5a.5.5 0 0 1-.998.06l-.5-8.5Zm6.53-.528a.5.5 0 0 1 .47.528l-.5 8.5a.5.5 0 1 1-.998-.058l.5-8.5a.5.5 0 0 1 .528-.47ZM8 4.5a.5.5 0 0 1 .5.5v8.5a.5.5 0 0 1-1 0V5a.5.5 0 0 1 .5-.5Z"/>
        </svg>
    </div>
</div>

<style>
    .todo {
        background: #eee;
        border-radius: 4px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        height: 40px;
        padding: 0 10px;
        padding-right: 0;
        overflow: hidden;
    }
    .todo .text {
        font-size: 13px;
        font-weight: 500;
    }
    .todo .remove {
        visibility: hidden;
        opacity: 0;
        transition: .3s all ease;
        cursor: pointer;
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        background: red;
        width: 40px;
    }
    .todo:hover .remove {
        visibility: visible;
        opacity: 1;
    }
</style>