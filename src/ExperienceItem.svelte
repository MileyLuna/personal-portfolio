<script>
    export let items = [];
    export let activeTabValue = 1;

    const handleClick = (tabValue) => () => (activeTabValue = tabValue);
</script>

<div class="backdrop" on:click|self>
    <div class="modal">
        <ul>
            {#each items as item}
                <li class={activeTabValue === item.value ? "active" : ""}>
                    <span on:click={handleClick(item.value)}></span>
                </li>
            {/each}
        </ul>
        {#each items as item}
            {#if activeTabValue == item.value}
                <div class="box">
                    <svelte:component this={item.component} />
                </div>
            {/if}
        {/each}
    </div>
</div>

<style>
    .backdrop {
        width: 100%;
        height: 100%;
        position: fixed;
        /* background: rgba(0, 0, 0, 0.8); */
    }
    .modal {
        padding: 10px;
        border-radius: 10px;
        max-width: 50%;
        margin: 10% auto;
        text-align: left;
        color: gray;
        /* background: rgb(252, 233, 233); */
    }
    .box {
        margin-bottom: 10px;
        padding: 40px;
        /* border: 1px solid #dee2e6; */
        border-radius: 0 0 0.5rem 0.5rem;
        border-top: 0;
    }
    ul {
        display: flex;
        flex-wrap: wrap;
        padding-left: 0;
        margin-bottom: 0;
        list-style: none;

        /* border-bottom: 1px solid #dee2e6; */
    }
    li {
        margin-bottom: -1px;
    }

    span {
        border: 1px solid transparent;
        border-radius: 50%;
        display: block;
        margin-left: 2rem;
        padding: .75rem .75rem;
        cursor: pointer;
        background-color: aqua;

    }

    span:hover {
        border-color: #e9ecef #e9ecef #dee2e6;
    }

    li.active > span {
        color: #495057;
        background-color: #fff;
        border-color: #dee2e6 #dee2e6 #fff;
    }
</style>
